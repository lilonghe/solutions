<script>
  import Tags from './lib/Tags.svelte';

  let solutionList = [
    {
      name: 'React 权限检查',
      featureList: ['提供 Auth 组件', '提供 useAuth hook', '提供 React-Router 路由守卫案例'],
      repository: 'https://stackblitz.com/edit/vitejs-vite-7nrbfd',
      tags: ['React', '权限']
    },
    {
      name: 'Vue3 权限检查',
      featureList: ['提供 Auth 组件', '提供 useAuth hook', '提供 Vue-Router 路由守卫案例'],
      repository: 'https://stackblitz.com/edit/vitejs-vite-yk5qlg',
      tags: ['Vue3', '权限']
    },
    {
      name: 'Webpack 实时 Mock',
      featureList: ['实时更新 Mock 信息','可以获取请求信息填充返回', '支持 JS 和 JSON 两种配置方式'],
      repository: 'https://github.com/lilonghe/solution-frontend-mockdata',
      tags: ['Webpack', 'Mock']
    }
  ]

  let tags = solutionList.reduce((tags, item) => {
    tags = tags.concat(item.tags);
    return tags;
  },[])
  tags = tags.filter((item, i) => {
    return tags.indexOf(item) === i;
  });

  $: activeTags = [];
  $: filterSolutionList = solutionList.filter(item => {
    if (!activeTags.length) return true;
    if (item.tags.some(tag => activeTags.includes(tag))) {
      return true;
    }
    return false;
  })

  function handleClick(event) {
    const selectTag = event.detail.detail;
    if (activeTags.includes(selectTag)) {
      activeTags = activeTags.filter(item => item !== selectTag);
    } else {
      activeTags = [...activeTags, selectTag];
    }
  }
</script>

<main>
  <div>
    <div class="filters">
      <Tags tags={tags} bind:activeTags={activeTags} on:click={handleClick} />
    </div>
    <div class="solution-list">
      {#each filterSolutionList as item}
        <a href="{item.repository}" target="_blank">
          <div class="solution">
            <h3>{item.name}</h3>
            <ul class="feature-list">
              {#each item.featureList as feature}
                <li>{feature}</li>
              {/each}
            </ul>
            <Tags tags={item.tags} />
          </div>
        </a>
      {/each}
    </div>
  </div>
</main>

<style>
  .solution-list {
    display: flex;
    gap: 20px;
    flex-wrap: wrap;
  }

  .solution {
    padding: 20px 40px;
    border: 1px solid #CCC;
    border-radius: 4px;
    width: 220px;
    height: 140px;
    display: flex;
    flex-direction: column;
  }

  .solution h3 {
    margin-top: 0;
    margin-bottom: 10px;
  }

  .feature-list {
    font-size: 12px;
    overflow-y: scroll;
    margin-bottom: 10px;
    flex: 1;
  }

  .filters {
    margin-bottom: 20px;
  }

  @media (max-width: 568px) { 
    .solution-list {
      flex-direction: column;
    }

    .solution {
      flex: 1;
      width: auto;
    }
  }
</style>
