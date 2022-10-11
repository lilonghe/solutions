<script>
  import Tags from './lib/Tags.svelte';

  let solutionList = [
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
</script>

<main>
  <div>
    <div class="solution-list">
      {#each solutionList as item}
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
    height: 160px;
    display: flex;
    flex-direction: column;
  }

  .feature-list {
    font-size: 12px;
    overflow-y: scroll;
    margin-bottom: 10px;
    height: 70px;
  }
</style>
