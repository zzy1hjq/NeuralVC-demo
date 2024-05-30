<template>
  <div id="app" class="container">
    <div class="h1-realtime">
      <h1>实时语音转换</h1>
    </div>


    <div class="h2-realtime-seen2seen">
      <h2>可见-可见：目标语音来自VCTK语音数据集 {{ tgt1.slice(-12) }}</h2>
      <div style="position: fixed; top: 65px; left: 600px;">
        <audio controls :src="tgt1" type="audio/wav"></audio>
      </div>
    </div>

    <div class="realtime-display-seen2seen">
      <el-table :data="nvc_seen2seen" style="width: 100%">
      <el-table-column prop="no" label="No" width="50" />
      <el-table-column label="Source" width="500">
        <template #default="{ row }">
          <audio controls :src="row.source" type="audio/wav"></audio>
          {{ row.source.slice(-12) }}
        </template>
      </el-table-column>
      <el-table-column label="NeuralVC" width="500">
        <template #default="{ row }">
          <audio controls :src="row.neuralvc" type="audio/wav"></audio>
          {{ row.neuralvc.slice(-21) }}
        </template>
      </el-table-column>
    </el-table>
    </div>


    <div class="h2-realtime-unseen2seen">
      <h2>不可见-可见：目标语音来自VCTK语音数据集 {{ tgt2.slice(-12) }}</h2>
      <div style="position: fixed; top: 565px; left: 620px;">
        <audio controls :src="tgt2" type="audio/wav"></audio>
      </div>
    </div>
    <div class="realtime-display-unseen2seen">
      <el-table :data="nvc_unseen2seen" style="width: 100%">
      <el-table-column prop="no" label="No" width="50" />
      <el-table-column label="Source" width="500">
        <template #default="{ row }">
          <audio controls :src="row.source" type="audio/wav"></audio>
          {{ row.source.slice(-12) }}
        </template>
      </el-table-column>
      <el-table-column label="NeuralVC" width="500">
        <template #default="{ row }">
          <audio controls :src="row.neuralvc" type="audio/wav"></audio>
          {{ row.neuralvc.slice(-21) }}
        </template>
      </el-table-column>
    </el-table>
    </div>


    <div class="h3-realtime-unseen2unseen">
      <h2>不可见-可见：目标语音来自VCTK语音数据集 {{ tgt3.slice(-12) }}</h2>
      <div style="position: fixed; top: 1070px; left: 620px;">
        <audio controls :src="tgt3" type="audio/wav"></audio>
      </div>
    </div>
    <div class="realtime-display-unseen2unseen">
      <el-table :data="nvc_unseen2unseen" style="width: 100%">
      <el-table-column prop="no" label="No" width="50" />
      <el-table-column label="Source" width="500">
        <template #default="{ row }">
          <audio controls :src="row.source" type="audio/wav"></audio>
          {{ row.source.slice(-12) }}
        </template>
      </el-table-column>
      <el-table-column label="NeuralVC" width="500">
        <template #default="{ row }">
          <audio controls :src="row.neuralvc" type="audio/wav"></audio>
          {{ row.neuralvc.slice(-21) }}
        </template>
      </el-table-column>
    </el-table>
    </div>

    <div class="line1"></div>

    <div class="h2-realtime">
      <h1>跨语言语音转换</h1>
    </div>
  </div>
</template>



<script>
export default {
  data() {
    return {
      title: '您的标题',
      nvc_seen2seen: [
      { no: 1, 
          source: "./nvc-seen2seen/src_p237_010.wav", 
          neuralvc: "./nvc-seen2seen/p237_010-p225_001.wav" },
      { no: 2, 
          source: "./nvc-seen2seen/src_p239_012.wav", 
          neuralvc: "./nvc-seen2seen/p239_012-p225_001.wav" },
      { no: 3, 
          source: "./nvc-seen2seen/src_p243_005.wav", 
          neuralvc: "./nvc-seen2seen/p243_005-p225_001.wav" },
      { no: 4, 
          source: "./nvc-seen2seen/src_p249_016.wav", 
          neuralvc: "./nvc-seen2seen/p249_016-p225_001.wav" },
      { no: 5, 
          source: "./nvc-seen2seen/src_p255_003.wav", 
          neuralvc: "./nvc-seen2seen/p255_003-p225_001.wav" },
        // Add more data as needed
      ],
      tgt1: "./nvc-seen2seen/tgt_p225_001.wav",

      nvc_unseen2seen: [
      { no: 1, 
          source: "./nvc-unseen2seen/src_174-168635-0000.wav", 
          neuralvc: "./nvc-unseen2seen/174-168635-0000-p234_020.wav" },
      { no: 2, 
          source: "./nvc-unseen2seen/src_2412-153948-0003.wav", 
          neuralvc: "./nvc-unseen2seen/2412-153948-0003-p234_020.wav" },
      { no: 3, 
          source: "./nvc-unseen2seen/src_3536-23268-0015.wav", 
          neuralvc: "./nvc-unseen2seen/3536-23268-0015-p234_020.wav" },
      { no: 4, 
          source: "./nvc-unseen2seen/src_5694-64038-0004.wav", 
          neuralvc: "./nvc-unseen2seen/5694-64038-0004-p234_020.wav" },
      { no: 5, 
          source: "./nvc-unseen2seen/src_6319-57405-0012.wav", 
          neuralvc: "./nvc-unseen2seen/6319-57405-0012-p234_020.wav" },
        // Add more data as needed
      ],
      tgt2: "./nvc-unseen2seen/tgt_p234_020.wav",

      nvc_unseen2unseen: [
      { no: 1, 
          source: "./nvc-unseen2unseen/src_84-121550-0008.wav", 
          neuralvc: "./nvc-unseen2unseen/84-121550-0008-174-168635-0000.wav" },
      { no: 2, 
          source: "./nvc-unseen2unseen/src_251-136532-0003.wav", 
          neuralvc: "./nvc-unseen2unseen/251-136532-0003-174-168635-0000.wav" },
      { no: 3, 
          source: "./nvc-unseen2unseen/src_777-126732-0018.wav", 
          neuralvc: "./nvc-unseen2unseen/777-126732-0018-174-168635-0000.wav" },
      { no: 4, 
          source: "./nvc-unseen2unseen/src_1462-170145-0006.wav", 
          neuralvc: "./nvc-unseen2unseen/1462-170145-0006-174-168635-0000.wav" },
      { no: 5, 
          source: "./nvc-unseen2unseen/src_5338-284437-0003.wav", 
          neuralvc: "./nvc-unseen2unseen/5338-284437-0003-174-168635-0000.wav" },
        // Add more data as needed
      ],
      tgt3: "./nvc-unseen2unseen/tgt_174-168635-0000.wav"
    };
  }
};
</script>


<style>
.scrollbar-demo-item {
  display: flex;
  align-items: center;
  justify-content: center;
  height: 50px;
  margin: 10px;
  text-align: center;
  border-radius: 4px;
  background: var(--el-color-primary-light-9);
  color: var(--el-color-primary);
}

.container {
  max-height: 100vh; /* 100vh 表示视窗的100%，你可以根据需要调整 */
  overflow-y: auto; /* 当内容超出容器高度时显示滚动条 */
}


.audio-card {
  margin-bottom: 20px;
}

.h1-realtime{
  position: fixed;
  top: 15px;
  left: 20px;
}


.line1 {
  float: right;
  width: 100%; 
  height: 5px; 
  position: fixed;
  background-color: grey; 
  top: 1580px;
  left: 15px;
  right: 10px;
}

.h2-realtime-seen2seen{
  position: fixed;
  top: 75px;
  left: 20px;
}

.realtime-display-seen2seen{
  position: fixed;
  top: 120px;
  left: 20px;
}

.h2-realtime-unseen2seen{
  position: fixed;
  top: 570px;
  left: 20px;
}

.realtime-display-unseen2seen{
  position: fixed;
  top: 630px;
  left: 20px;
}

.h3-realtime-unseen2unseen{
  position: fixed;
  top: 1080px;
  left: 20px;
}


.realtime-display-unseen2unseen{
  position: fixed;
  top: 1130px;
  left: 20px;
}

.h2-realtime{
  position: fixed;
  top: 1600px;
  left: 20px;
}

</style>
