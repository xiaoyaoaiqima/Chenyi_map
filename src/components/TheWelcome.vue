<script setup lang="ts">
import { ElCard } from 'element-plus';
</script>

<template>
  <div class="container">
    <ElCard class="background">
      <WelcomeItem>
        <template #icon>
          <DocumentationIcon />
        </template>
        <h1>中国革命事业</h1>
        <p> 陈毅将军是中国革命事业的重要人物之一，他在中国共产党和人民解放军中发挥了重要作用。他积极参与革命斗争，为实现中国的独立和解放做出了巨大贡献。</p>

        <h1>陈毅将军的事迹</h1>
        <p>陈毅将军参与了中国共产党的早期组织工作，是红军的重要领导人之一。 <br />他在抗日战争和解放战争中表现出色，为中国革命的胜利做出了重要贡献。</p>
        <p>他坚定的信念、勇敢的精神和卓越的领导能力，使他成为中国革命的杰出代表。</p>

        <br>
        <hr>
        <p> 陈毅将军的事迹值得我们学习和纪念，他为中国的独立、民主和社会主义事业做出了不可磨灭的贡献。</p>

      </WelcomeItem>
    </ElCard>
  </div>
</template>

<style>
.container {
  display: flex;
  justify-content: center;
  align-items: center;
}

.background {
  background-color: rgba(0, 0, 0, 0.5);
  padding: 20px;
  color: white;
}
</style>