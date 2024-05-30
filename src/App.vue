<template>
  <div id="app" class="container">
    <div class="h1-realtime">
      <h1>实时语音转换</h1>
    </div>


    <div class="h2-realtime-seen2seen">
      <h2>可见-可见：目标语音来自VCTK语音数据集 {{ tgt1.slice(-12) }}</h2>
      <div style="position: absolute; top: -7px; left: 600px;">
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
          {{ row.time1 }}
        </template>
      </el-table-column>
      <el-table-column label="VITS-ISTFT" width="500">
        <template #default="{ row }">
          <audio controls :src="row.istft" type="audio/wav"></audio>
          {{ row.time2 }}
        </template>
      </el-table-column>
      <el-table-column label="VITS-HifiGAN" width="500">
        <template #default="{ row }">
          <audio controls :src="row.hifigan" type="audio/wav"></audio>
          {{ row.time3 }}
        </template>
      </el-table-column>
    </el-table>
    </div>


    <div class="h2-realtime-unseen2seen">
      <h2>不可见-可见：目标语音来自VCTK语音数据集 {{ tgt2.slice(-12) }}</h2>
      <div style="position: absolute; top: 0px; left: 620px;">
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
          {{ row.time1 }}
        </template>
      </el-table-column>
      <el-table-column label="VITS-ISTFT" width="500">
        <template #default="{ row }">
          <audio controls :src="row.istft" type="audio/wav"></audio>
          {{ row.time2 }}
        </template>
      </el-table-column>
      <el-table-column label="VITS-HifiGAN" width="500">
        <template #default="{ row }">
          <audio controls :src="row.hifigan" type="audio/wav"></audio>
          {{ row.time3 }}
        </template>
      </el-table-column>
    </el-table>
    </div>


    <div class="h3-realtime-unseen2unseen">
      <h2>不可见-不可见：目标语音来自LibriTTS语音数据集 {{ tgt3.slice(-12) }}</h2>
      <div style="position: absolute; top: -5px; left: 640px;">
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
          {{ row.time1 }}
        </template>
      </el-table-column>
      <el-table-column label="VITS-ISTFT" width="500">
        <template #default="{ row }">
          <audio controls :src="row.istft" type="audio/wav"></audio>
          {{ row.time2 }}
        </template>
      </el-table-column>
      <el-table-column label="VITS-HifiGAN" width="500">
        <template #default="{ row }">
          <audio controls :src="row.hifigan" type="audio/wav"></audio>
          {{ row.time3 }}
        </template>
      </el-table-column>
    </el-table>
    </div>

    <div class="line1"></div>

    <div class="h2-realtime">
      <h1>跨语言语音转换</h1>
    </div>

    <div class="xvc-title-seen2seen">
      <h2>可见-可见：目标语音来自VCTK语音数据集 {{ tgt4.slice(-12) }}</h2>
      <div style="position: absolute; top: -5px; left: 580px;">
        <audio controls :src="tgt4" type="audio/wav"></audio>
      </div>
    </div>


    <div class="xvc-display-seen2seen">
      <el-table :data="xvc_seen2seen" style="width: 100%">
      <el-table-column prop="no" label="No" width="50" />
      <el-table-column label="Source" width="500">
        <template #default="{ row }">
          <audio controls :src="row.source" type="audio/wav"></audio>
          {{ row.source.slice(-12) }}
        </template>
      </el-table-column>
      <el-table-column label="NeuralXVC" width="500">
        <template #default="{ row }">
          <audio controls :src="row.neuralxvc" type="audio/wav"></audio>
          {{ row.neuralxvc.slice(-21) }}
        </template>
      </el-table-column>
      <el-table-column label="ConsistencyXVC(English)" width="500">
        <template #default="{ row }">
          <audio controls :src="row.bl" type="audio/wav"></audio>
          {{ row.bl.slice(-21) }}
        </template>
      </el-table-column>
    </el-table>
    </div>


    <div class="xvc-title-unseen2seen">
      <h2>不可见-可见：目标语音来自VCTK语音数据集 {{ tgt5.slice(-12) }}</h2>
      <div style="position: absolute; top: -5px; left: 600px;">
        <audio controls :src="tgt5" type="audio/wav"></audio>
      </div>
    </div>

    <div class="xvc-display-unseen2seen">
      <el-table :data="xvc_unseen2seen" style="width: 100%">
      <el-table-column prop="no" label="No" width="50" />
      <el-table-column label="Source" width="500">
        <template #default="{ row }">
          <audio controls :src="row.source" type="audio/wav"></audio>
          {{ row.source.slice(-12) }}
        </template>
      </el-table-column>
      <el-table-column label="NeuralXVC" width="500">
        <template #default="{ row }">
          <audio controls :src="row.neuralxvc" type="audio/wav"></audio>
          {{ row.neuralxvc.slice(-21) }}
        </template>
      </el-table-column>
      <el-table-column label="ConsistencyXVC(English)" width="500">
        <template #default="{ row }">
          <audio controls :src="row.bl" type="audio/wav"></audio>
          {{ row.bl.slice(-21) }}
        </template>
      </el-table-column>
    </el-table>
    </div>

    <div class="xvc-title-unseen2unseen">
      <h2>可见-可见：目标语音来自LibriTTS语音数据集 {{ tgt6.slice(-12) }}</h2>
      <div style="position: absolute; top: -5px; left: 600px;">
        <audio controls :src="tgt6" type="audio/wav"></audio>
      </div>
    </div>


    <div class="xvc-display-unseen2unseen">
      <el-table :data="xvc_unseen2unseen" style="width: 100%">
      <el-table-column prop="no" label="No" width="50" />
      <el-table-column label="Source" width="500">
        <template #default="{ row }">
          <audio controls :src="row.source" type="audio/wav"></audio>
          {{ row.source.slice(-12) }}
        </template>
      </el-table-column>
      <el-table-column label="NeuralXVC" width="500">
        <template #default="{ row }">
          <audio controls :src="row.neuralxvc" type="audio/wav"></audio>
          {{ row.neuralxvc.slice(-21) }}
        </template>
      </el-table-column>
      <el-table-column label="ConsistencyXVC(English)" width="500">
        <template #default="{ row }">
          <audio controls :src="row.bl" type="audio/wav"></audio>
          {{ row.bl.slice(-21) }}
        </template>
      </el-table-column>
    </el-table>
    </div>


    <div class="xvc-title-esd">
      <h2>不同语言之间音色转换，目标语音来自ESD中文语音数据集 {{ tgt7.slice(-12) }}</h2>
      <div style="position: absolute; top: -5px; left: 730px;">
        <audio controls :src="tgt7" type="audio/wav"></audio>
      </div>
    </div>

    <div class="xvc-display-esd">
      <el-table :data="xvc_esd" style="width: 100%">
      <el-table-column prop="no" label="No" width="50" />
      <el-table-column label="Source" width="500">
        <template #default="{ row }">
          <audio controls :src="row.source" type="audio/wav"></audio>
          {{ row.source.slice(-12) }}
        </template>
      </el-table-column>
      <el-table-column label="NeuralXVC" width="500">
        <template #default="{ row }">
          <audio controls :src="row.xvc" type="audio/wav"></audio>
          {{ row.xvc.slice(-21) }}
        </template>
      </el-table-column>
      <el-table-column label="w/o F0Pred" width="500">
        <template #default="{ row }">
          <audio controls :src="row.nvc" type="audio/wav"></audio>
          {{ row.nvc.slice(-21) }}
        </template>
      </el-table-column>
      <el-table-column label="ConsistencyXVC(English)" width="500">
        <template #default="{ row }">
          <audio controls :src="row.bl" type="audio/wav"></audio>
          {{ row.bl.slice(-21) }}
        </template>
      </el-table-column>
    </el-table>
    </div>

    <div class="xvc-title-jvs">
      <h2>不同语言之间音色转换，目标语音来自JVS日语语音数据集 {{ tgt8.slice(-12) }}</h2>
      <div style="position: absolute; top: -5px; left: 730px;">
        <audio controls :src="tgt8" type="audio/wav"></audio>
      </div>
    </div>

    <div class="xvc-display-jvs">
      <el-table :data="xvc_jvs" style="width: 100%">
      <el-table-column prop="no" label="No" width="50" />
      <el-table-column label="Source" width="500">
        <template #default="{ row }">
          <audio controls :src="row.source" type="audio/wav"></audio>
          {{ row.source.slice(-12) }}
        </template>
      </el-table-column>
      <el-table-column label="NeuralXVC" width="500">
        <template #default="{ row }">
          <audio controls :src="row.xvc" type="audio/wav"></audio>
          {{ row.xvc.slice(-21) }}
        </template>
      </el-table-column>
      <el-table-column label="w/o F0Pred" width="500">
        <template #default="{ row }">
          <audio controls :src="row.nvc" type="audio/wav"></audio>
          {{ row.nvc.slice(-21) }}
        </template>
      </el-table-column>
      <el-table-column label="ConsistencyXVC(English)" width="500">
        <template #default="{ row }">
          <audio controls :src="row.bl" type="audio/wav"></audio>
          {{ row.bl.slice(-21) }}
        </template>
      </el-table-column>
    </el-table>
    </div>

    
    <div class="xvc-title-libritts">
      <h2>不同语言之间音色转换，目标语音来自LiBritts英语语音数据集 {{ tgt9.slice(-12) }}</h2>
      <div style="position: absolute; top: -5px; left: 760px;">
        <audio controls :src="tgt9" type="audio/wav"></audio>
      </div>
    </div>

    <div class="xvc-display-libritts">
      <el-table :data="xvc_libritts" style="width: 100%">
      <el-table-column prop="no" label="No" width="50" />
      <el-table-column label="Source" width="500">
        <template #default="{ row }">
          <audio controls :src="row.source" type="audio/wav"></audio>
          {{ row.source.slice(-12) }}
        </template>
      </el-table-column>
      <el-table-column label="NeuralXVC" width="500">
        <template #default="{ row }">
          <audio controls :src="row.xvc" type="audio/wav"></audio>
          {{ row.xvc.slice(-21) }}
        </template>
      </el-table-column>
      <el-table-column label="w/o F0Pred" width="500">
        <template #default="{ row }">
          <audio controls :src="row.nvc" type="audio/wav"></audio>
          {{ row.nvc.slice(-21) }}
        </template>
      </el-table-column>
      <el-table-column label="ConsistencyXVC(English)" width="500">
        <template #default="{ row }">
          <audio controls :src="row.bl" type="audio/wav"></audio>
          {{ row.bl.slice(-21) }}
        </template>
      </el-table-column>
    </el-table>
    </div>

    <div class="xvc-title-zeroth">
      <h2>不同语言之间音色转换，目标语音来自ZeroTh韩语语音数据集 {{ tgt10.slice(-12) }}</h2>
      <div style="position: absolute; top: -5px; left: 760px;">
        <audio controls :src="tgt10" type="audio/wav"></audio>
      </div>
    </div>

    <div class="xvc-display-zeroth">
      <el-table :data="xvc_zeroth" style="width: 100%">
      <el-table-column prop="no" label="No" width="50" />
      <el-table-column label="Source" width="500">
        <template #default="{ row }">
          <audio controls :src="row.source" type="audio/wav"></audio>
          {{ row.source.slice(-12) }}
        </template>
      </el-table-column>
      <el-table-column label="NeuralXVC" width="500">
        <template #default="{ row }">
          <audio controls :src="row.xvc" type="audio/wav"></audio>
          {{ row.xvc.slice(-21) }}
        </template>
      </el-table-column>
      <el-table-column label="w/o F0Pred" width="500">
        <template #default="{ row }">
          <audio controls :src="row.nvc" type="audio/wav"></audio>
          {{ row.nvc.slice(-21) }}
        </template>
      </el-table-column>
      <el-table-column label="ConsistencyXVC(English)" width="500">
        <template #default="{ row }">
          <audio controls :src="row.bl" type="audio/wav"></audio>
          {{ row.bl.slice(-21) }}
        </template>
      </el-table-column>
    </el-table>
    </div>


    <div class="xvc-title-zeroth-same">
      <h2>相同语言之间音色转换，目标语音来自Zeroth韩语语音数据集 {{ tgt11.slice(-12) }}</h2>
      <div style="position: absolute; top: -5px; left: 760px;">
        <audio controls :src="tgt11" type="audio/wav"></audio>
      </div>
    </div>

    <div class="xvc-display-zeroth-same">
      <el-table :data="xvc_zeroth_same" style="width: 100%">
      <el-table-column prop="no" label="No" width="50" />
      <el-table-column label="Source" width="500">
        <template #default="{ row }">
          <audio controls :src="row.source" type="audio/wav"></audio>
          {{ row.source.slice(-12) }}
        </template>
      </el-table-column>
      <el-table-column label="NeuralXVC" width="500">
        <template #default="{ row }">
          <audio controls :src="row.xvc" type="audio/wav"></audio>
          {{ row.xvc.slice(-21) }}
        </template>
      </el-table-column>
      <el-table-column label="w/o F0Pred" width="500">
        <template #default="{ row }">
          <audio controls :src="row.nvc" type="audio/wav"></audio>
          {{ row.nvc.slice(-21) }}
        </template>
      </el-table-column>
      <el-table-column label="ConsistencyXVC(English)" width="500">
        <template #default="{ row }">
          <audio controls :src="row.bl" type="audio/wav"></audio>
          {{ row.bl.slice(-21) }}
        </template>
      </el-table-column>
    </el-table>
    </div>


    <div class="xvc-title-jvs-same">
      <h2>相同语言之间音色转换，目标语音来自JVS日语语音数据集 {{ tgt12.slice(-12) }}</h2>
      <div style="position: absolute; top: -5px; left: 760px;">
        <audio controls :src="tgt12" type="audio/wav"></audio>
      </div>
    </div>

    <div class="xvc-display-jvs-same">
      <el-table :data="xvc_jvs_same" style="width: 100%">
      <el-table-column prop="no" label="No" width="50" />
      <el-table-column label="Source" width="500">
        <template #default="{ row }">
          <audio controls :src="row.source" type="audio/wav"></audio>
          {{ row.source.slice(-12) }}
        </template>
      </el-table-column>
      <el-table-column label="NeuralXVC" width="500">
        <template #default="{ row }">
          <audio controls :src="row.xvc" type="audio/wav"></audio>
          {{ row.xvc.slice(-21) }}
        </template>
      </el-table-column>
      <el-table-column label="w/o F0Pred" width="500">
        <template #default="{ row }">
          <audio controls :src="row.nvc" type="audio/wav"></audio>
          {{ row.nvc.slice(-21) }}
        </template>
      </el-table-column>
      <el-table-column label="ConsistencyXVC(English)" width="500">
        <template #default="{ row }">
          <audio controls :src="row.bl" type="audio/wav"></audio>
          {{ row.bl.slice(-21) }}
        </template>
      </el-table-column>
    </el-table>
    </div>


    <div class="xvc-title-esd-same">
      <h2>相同语言之间音色转换，目标语音来自ESD中文语音数据集 {{ tgt13.slice(-12) }}</h2>
      <div style="position: absolute; top: -5px; left: 760px;">
        <audio controls :src="tgt13" type="audio/wav"></audio>
      </div>
    </div>

    <div class="xvc-display-esd-same">
      <el-table :data="xvc_esd_same" style="width: 100%">
      <el-table-column prop="no" label="No" width="50" />
      <el-table-column label="Source" width="500">
        <template #default="{ row }">
          <audio controls :src="row.source" type="audio/wav"></audio>
          {{ row.source.slice(-12) }}
        </template>
      </el-table-column>
      <el-table-column label="NeuralXVC" width="500">
        <template #default="{ row }">
          <audio controls :src="row.xvc" type="audio/wav"></audio>
          {{ row.xvc.slice(-21) }}
        </template>
      </el-table-column>
      <el-table-column label="w/o F0Pred" width="500">
        <template #default="{ row }">
          <audio controls :src="row.nvc" type="audio/wav"></audio>
          {{ row.nvc.slice(-21) }}
        </template>
      </el-table-column>
      <el-table-column label="ConsistencyXVC(English)" width="500">
        <template #default="{ row }">
          <audio controls :src="row.bl" type="audio/wav"></audio>
          {{ row.bl.slice(-21) }}
        </template>
      </el-table-column>
    </el-table>
    </div>


    <div class="line2"></div>
    <div class="h3-evc">
      <h1>表达性语音转换</h1>
    </div>

    <div class="evc-title-evc-angry">
      <h2>可见：生气情绪语音来自ESD英文语音数据集 {{ tgt14.slice(-12) }}</h2>
      <div style="position: absolute; top: -5px; left: 660px;">
        <audio controls :src="tgt14" type="audio/wav"></audio>
      </div>
    </div>

    <div class="evc-display-evc-angry">
      <el-table :data="evc_angry" style="width: 100%">
      <el-table-column prop="no" label="No" width="50" />
      <el-table-column label="Source" width="500">
        <template #default="{ row }">
          <audio controls :src="row.source" type="audio/wav"></audio>
          {{ row.source.slice(-12) }}
        </template>
      </el-table-column>
      <el-table-column label="NeuralEVC" width="500">
        <template #default="{ row }">
          <audio controls :src="row.evc" type="audio/wav"></audio>
          {{ row.evc.slice(-21) }}
        </template>
      </el-table-column>
      <el-table-column label="w/o Loss" width="500">
        <template #default="{ row }">
          <audio controls :src="row.nvc" type="audio/wav"></audio>
          {{ row.nvc.slice(-21) }}
        </template>
      </el-table-column>
    </el-table>
    </div>

    <div class="evc-title-evc-happy">
      <h2>可见：开心情绪语音来自ESD英文语音数据集 {{ tgt15.slice(-12) }}</h2>
      <div style="position: absolute; top: -5px; left: 660px;">
        <audio controls :src="tgt15" type="audio/wav"></audio>
      </div>
    </div>

    <div class="evc-display-evc-happy">
      <el-table :data="evc_happy" style="width: 100%">
      <el-table-column prop="no" label="No" width="50" />
      <el-table-column label="Source" width="500">
        <template #default="{ row }">
          <audio controls :src="row.source" type="audio/wav"></audio>
          {{ row.source.slice(-12) }}
        </template>
      </el-table-column>
      <el-table-column label="NeuralEVC" width="500">
        <template #default="{ row }">
          <audio controls :src="row.evc" type="audio/wav"></audio>
          {{ row.evc.slice(-21) }}
        </template>
      </el-table-column>
      <el-table-column label="w/o Loss" width="500">
        <template #default="{ row }">
          <audio controls :src="row.nvc" type="audio/wav"></audio>
          {{ row.nvc.slice(-21) }}
        </template>
      </el-table-column>
    </el-table>
    </div>


    <div class="evc-title-evc-neutral">
      <h2>可见：中性情绪语音来自ESD英文语音数据集 {{ tgt16.slice(-12) }}</h2>
      <div style="position: absolute; top: -5px; left: 660px;">
        <audio controls :src="tgt16" type="audio/wav"></audio>
      </div>
    </div>

    <div class="evc-display-evc-neutral">
      <el-table :data="evc_neutral" style="width: 100%">
      <el-table-column prop="no" label="No" width="50" />
      <el-table-column label="Source" width="500">
        <template #default="{ row }">
          <audio controls :src="row.source" type="audio/wav"></audio>
          {{ row.source.slice(-12) }}
        </template>
      </el-table-column>
      <el-table-column label="NeuralEVC" width="500">
        <template #default="{ row }">
          <audio controls :src="row.evc" type="audio/wav"></audio>
          {{ row.evc.slice(-21) }}
        </template>
      </el-table-column>
      <el-table-column label="w/o Loss" width="500">
        <template #default="{ row }">
          <audio controls :src="row.nvc" type="audio/wav"></audio>
          {{ row.nvc.slice(-21) }}
        </template>
      </el-table-column>
    </el-table>
    </div>


    <div class="evc-title-evc-sad">
      <h2>可见：伤心情绪语音来自ESD英文语音数据集 {{ tgt17.slice(-12) }}</h2>
      <div style="position: absolute; top: -5px; left: 660px;">
        <audio controls :src="tgt17" type="audio/wav"></audio>
      </div>
    </div>

    <div class="evc-display-evc-sad">
      <el-table :data="evc_sad" style="width: 100%">
      <el-table-column prop="no" label="No" width="50" />
      <el-table-column label="Source" width="500">
        <template #default="{ row }">
          <audio controls :src="row.source" type="audio/wav"></audio>
          {{ row.source.slice(-12) }}
        </template>
      </el-table-column>
      <el-table-column label="NeuralEVC" width="500">
        <template #default="{ row }">
          <audio controls :src="row.evc" type="audio/wav"></audio>
          {{ row.evc.slice(-21) }}
        </template>
      </el-table-column>
      <el-table-column label="w/o Loss" width="500">
        <template #default="{ row }">
          <audio controls :src="row.nvc" type="audio/wav"></audio>
          {{ row.nvc.slice(-21) }}
        </template>
      </el-table-column>
    </el-table>
    </div>

    <div class="evc-title-emo-angry">
      <h2>不可见：生气情绪语音来自EmoEV英文语音数据集 {{ tgt18.slice(-12) }}</h2>
      <div style="position: absolute; top: -5px; left: 660px;">
        <audio controls :src="tgt18" type="audio/wav"></audio>
      </div>
    </div>

    <div class="evc-display-emo-angry">
      <el-table :data="evc_emo_angry" style="width: 100%">
      <el-table-column prop="no" label="No" width="50" />
      <el-table-column label="Source" width="500">
        <template #default="{ row }">
          <audio controls :src="row.source" type="audio/wav"></audio>
          {{ row.source.slice(-12) }}
        </template>
      </el-table-column>
      <el-table-column label="NeuralEVC" width="500">
        <template #default="{ row }">
          <audio controls :src="row.evc" type="audio/wav"></audio>
          {{ row.evc.slice(-21) }}
        </template>
      </el-table-column>
      <el-table-column label="w/o Loss" width="500">
        <template #default="{ row }">
          <audio controls :src="row.nvc" type="audio/wav"></audio>
          {{ row.nvc.slice(-21) }}
        </template>
      </el-table-column>
    </el-table>
    </div>


    <div class="evc-title-emo-disgust">
      <h2>不可见：忧虑情绪语音来自EmoEV英文语音数据集 {{ tgt19.slice(-12) }}</h2>
      <div style="position: absolute; top: -5px; left: 660px;">
        <audio controls :src="tgt19" type="audio/wav"></audio>
      </div>
    </div>

    <div class="evc-display-emo-disgust">
      <el-table :data="evc_emo_disgust" style="width: 100%">
      <el-table-column prop="no" label="No" width="50" />
      <el-table-column label="Source" width="500">
        <template #default="{ row }">
          <audio controls :src="row.source" type="audio/wav"></audio>
          {{ row.source.slice(-12) }}
        </template>
      </el-table-column>
      <el-table-column label="NeuralEVC" width="500">
        <template #default="{ row }">
          <audio controls :src="row.evc" type="audio/wav"></audio>
          {{ row.evc.slice(-21) }}
        </template>
      </el-table-column>
      <el-table-column label="w/o Loss" width="500">
        <template #default="{ row }">
          <audio controls :src="row.nvc" type="audio/wav"></audio>
          {{ row.nvc.slice(-21) }}
        </template>
      </el-table-column>
    </el-table>
    </div>

    <div class="evc-title-emo-happy">
      <h2>不可见：开心情绪语音来自EmoEV英文语音数据集 {{ tgt20.slice(-12) }}</h2>
      <div style="position: absolute; top: -5px; left: 660px;">
        <audio controls :src="tgt20" type="audio/wav"></audio>
      </div>
    </div>

    <div class="evc-display-emo-happy">
      <el-table :data="evc_emo_happy" style="width: 100%">
      <el-table-column prop="no" label="No" width="50" />
      <el-table-column label="Source" width="500">
        <template #default="{ row }">
          <audio controls :src="row.source" type="audio/wav"></audio>
          {{ row.source.slice(-12) }}
        </template>
      </el-table-column>
      <el-table-column label="NeuralEVC" width="500">
        <template #default="{ row }">
          <audio controls :src="row.evc" type="audio/wav"></audio>
          {{ row.evc.slice(-21) }}
        </template>
      </el-table-column>
      <el-table-column label="w/o Loss" width="500">
        <template #default="{ row }">
          <audio controls :src="row.nvc" type="audio/wav"></audio>
          {{ row.nvc.slice(-21) }}
        </template>
      </el-table-column>
    </el-table>
    </div>


    <div class="evc-title-emo-neutral">
      <h2>不可见：中性情绪语音来自EmoEV英文语音数据集 {{ tgt21.slice(-12) }}</h2>
      <div style="position: absolute; top: -5px; left: 660px;">
        <audio controls :src="tgt21" type="audio/wav"></audio>
      </div>
    </div>

    <div class="evc-display-emo-neutral">
      <el-table :data="evc_emo_neutral" style="width: 100%">
      <el-table-column prop="no" label="No" width="50" />
      <el-table-column label="Source" width="500">
        <template #default="{ row }">
          <audio controls :src="row.source" type="audio/wav"></audio>
          {{ row.source.slice(-12) }}
        </template>
      </el-table-column>
      <el-table-column label="NeuralEVC" width="500">
        <template #default="{ row }">
          <audio controls :src="row.evc" type="audio/wav"></audio>
          {{ row.evc.slice(-21) }}
        </template>
      </el-table-column>
      <el-table-column label="w/o Loss" width="500">
        <template #default="{ row }">
          <audio controls :src="row.nvc" type="audio/wav"></audio>
          {{ row.nvc.slice(-21) }}
        </template>
      </el-table-column>
    </el-table>
    </div>




  </div>
</template>



<script>
export default {
  data() {
    return {
      title: '您的标题',
      // NVC
      nvc_seen2seen: [
      { no: 1, 
          source: "./nvc-seen2seen/src_p237_010.wav", 
          neuralvc: "./nvc-seen2seen/p237_010-p225_001.wav",
          nvc: "./nvc-seen2seen/nvc_p237_010-p225_001.wav", 
          istft: "./nvc-seen2seen/istft_p237_010-p225_001.wav", 
          hifigan: "./nvc-seen2seen/hifi_p237_010-p225_001.wav" ,
          time1: "0.072s",
          time2: "0.223s",
          time3: "0.252s"},
      { no: 2, 
          source: "./nvc-seen2seen/src_p239_012.wav", 
          neuralvc: "./nvc-seen2seen/p239_012-p225_001.wav",
          nvc: "./nvc-seen2seen/nvc_p239_012-p225_001.wav", 
          istft: "./nvc-seen2seen/istft_p239_012-p225_001.wav", 
          hifigan: "./nvc-seen2seen/hifi_p239_012-p225_001.wav",
          time1: "0.051s",
          time2: "0.107s",
          time3: "0.240s"},
      { no: 3, 
          source: "./nvc-seen2seen/src_p243_005.wav", 
          neuralvc: "./nvc-seen2seen/p243_005-p225_001.wav" ,
          nvc: "./nvc-seen2seen/nvc_p243_005-p225_001.wav", 
          istft: "./nvc-seen2seen/istft_p243_005-p225_001.wav", 
          hifigan: "./nvc-seen2seen/hifi_p243_005-p225_001.wav" ,
          time1: "0.031s",
          time2: "0.111s",
          time3: "0.242s"},
      { no: 4, 
          source: "./nvc-seen2seen/src_p249_016.wav", 
          neuralvc: "./nvc-seen2seen/p249_016-p225_001.wav" ,
          nvc: "./nvc-seen2seen/nvc_p249_016-p225_001.wav", 
          istft: "./nvc-seen2seen/istft_p249_016-p225_001.wav", 
          hifigan: "./nvc-seen2seen/hifi_p249_016-p225_001.wav" ,
          time1: "0.029s",
          time2: "0.106s",
          time3: "0.222s"},
      { no: 5, 
          source: "./nvc-seen2seen/src_p255_003.wav", 
          neuralvc: "./nvc-seen2seen/p255_003-p225_001.wav" ,
          nvc: "./nvc-seen2seen/nvc_p255_003-p225_001.wav", 
          istft: "./nvc-seen2seen/istft_p255_003-p225_001.wav", 
          hifigan: "./nvc-seen2seen/hifi_p255_003-p225_001.wav" ,
          time1: "0.030s",
          time2: "0.108s",
          time3: "0.220s"},
        // Add more data as needed
      ],
      tgt1: "./nvc-seen2seen/tgt_p225_001.wav",

      nvc_unseen2seen: [
      { no: 1, 
          source: "./nvc-unseen2seen/src_174-168635-0000.wav", 
          neuralvc: "./nvc-unseen2seen/174-168635-0000-p234_020.wav" ,
          nvc: "./nvc-unseen2seen/nvc_174-168635-0000-p234_020.wav", 
          istft: "./nvc-unseen2seen/istft_174-168635-0000-p234_020.wav", 
          hifigan: "./nvc-unseen2seen/hifi_174-168635-0000-p234_020.wav" ,
          time1: "0.074s",
          time2: "0.177s",
          time3: "0.251s"},
      { no: 2, 
          source: "./nvc-unseen2seen/src_2412-153948-0003.wav", 
          neuralvc: "./nvc-unseen2seen/2412-153948-0003-p234_020.wav" ,
          nvc: "./nvc-unseen2seen/nvc_2412-153948-0003-p234_020.wav", 
          istft: "./nvc-unseen2seen/istft_2412-153948-0003-p234_020.wav", 
          hifigan: "./nvc-unseen2seen/hifi_2412-153948-0003-p234_020.wav" ,
          time1: "0.058s",
          time2: "0.116s",
          time3: "0.189s"},
      { no: 3, 
          source: "./nvc-unseen2seen/src_3536-23268-0015.wav", 
          neuralvc: "./nvc-unseen2seen/3536-23268-0015-p234_020.wav" ,
          nvc: "./nvc-unseen2seen/nvc_3536-23268-0015-p234_020.wav", 
          istft: "./nvc-unseen2seen/istft_3536-23268-0015-p234_020.wav", 
          hifigan: "./nvc-unseen2seen/hifi_3536-23268-0015-p234_020.wav" ,
          time1: "0.039s",
          time2: "0.110s",
          time3: "0.186s"},
      { no: 4, 
          source: "./nvc-unseen2seen/src_5694-64038-0004.wav", 
          neuralvc: "./nvc-unseen2seen/5694-64038-0004-p234_020.wav" ,
          nvc: "./nvc-unseen2seen/nvc_5694-64038-0004-p234_020.wav", 
          istft: "./nvc-unseen2seen/istft_5694-64038-0004-p234_020.wav", 
          hifigan: "./nvc-unseen2seen/hifi_5694-64038-0004-p234_020.wav" ,
          time1: "0.048s",
          time2: "0.126s",
          time3: "0.191s"},
      { no: 5, 
          source: "./nvc-unseen2seen/src_6319-57405-0012.wav", 
          neuralvc: "./nvc-unseen2seen/6319-57405-0012-p234_020.wav" ,
          nvc: "./nvc-unseen2seen/nvc_6319-57405-0012-p234_020.wav", 
          istft: "./nvc-unseen2seen/istft_6319-57405-0012-p234_020.wav", 
          hifigan: "./nvc-unseen2seen/hifi_6319-57405-0012-p234_020.wav" ,
          time1: "0.046s",
          time2: "0.119s",
          time3: "0.192s"},
        // Add more data as needed
      ],
      tgt2: "./nvc-unseen2seen/tgt_p234_020.wav",

      nvc_unseen2unseen: [
      { no: 1, 
          source: "./nvc-unseen2unseen/src_84-121550-0008.wav", 
          neuralvc: "./nvc-unseen2unseen/84-121550-0008-174-168635-0000.wav" ,
          nvc: "./nvc-unseen2unseen/nvc_84-121550-0008-174-168635-0000.wav", 
          istft: "./nvc-unseen2unseen/istft_84-121550-0008-174-168635-0000.wav", 
          hifigan: "./nvc-unseen2unseen/hifi_84-121550-0008-174-168635-0000.wav" ,
          time1: "0.082s",
          time2: "0.081s",
          time3: "0.105s"},
      { no: 2, 
          source: "./nvc-unseen2unseen/src_251-136532-0003.wav", 
          neuralvc: "./nvc-unseen2unseen/251-136532-0003-174-168635-0000.wav" ,
          nvc: "./nvc-unseen2unseen/nvc_251-136532-0003-174-168635-0000.wav", 
          istft: "./nvc-unseen2unseen/istft_251-136532-0003-174-168635-0000.wav", 
          hifigan: "./nvc-unseen2unseen/hifi_251-136532-0003-174-168635-0000.wav" ,
          time1: "0.061s",
          time2: "0.139s",
          time3: "0.206s"},
      { no: 3, 
          source: "./nvc-unseen2unseen/src_777-126732-0018.wav", 
          neuralvc: "./nvc-unseen2unseen/777-126732-0018-174-168635-0000.wav" ,
          nvc: "./nvc-unseen2unseen/nvc_777-126732-0018-174-168635-0000.wav", 
          istft: "./nvc-unseen2unseen/istft_777-126732-0018-174-168635-0000.wav", 
          hifigan: "./nvc-unseen2unseen/hifi_777-126732-0018-174-168635-0000.wav" ,
          time1: "0.033s",
          time2: "0.110s",
          time3: "0.185s"},
      { no: 4, 
          source: "./nvc-unseen2unseen/src_1462-170145-0006.wav", 
          neuralvc: "./nvc-unseen2unseen/1462-170145-0006-174-168635-0000.wav" ,
          nvc: "./nvc-unseen2unseen/nvc_1462-170145-0006-174-168635-0000.wav", 
          istft: "./nvc-unseen2unseen/istft_1462-170145-0006-174-168635-0000.wav", 
          hifigan: "./nvc-unseen2unseen/hifi_1462-170145-0006-174-168635-0000.wav" ,
          time1: "0.041s",
          time2: "0.111s",
          time3: "0.188s"},
      { no: 5, 
          source: "./nvc-unseen2unseen/src_5338-284437-0003.wav", 
          neuralvc: "./nvc-unseen2unseen/5338-284437-0003-174-168635-0000.wav" ,
          nvc: "./nvc-unseen2unseen/nvc_5338-284437-0003-174-168635-0000.wav", 
          istft: "./nvc-unseen2unseen/istft_5338-284437-0003-174-168635-0000.wav", 
          hifigan: "./nvc-unseen2unseen/hifi_5338-284437-0003-174-168635-0000.wav" ,
          time1: "0.040s",
          time2: "0.117s",
          time3: "0.183s"},
        // Add more data as needed
      ],
      tgt3: "./nvc-unseen2unseen/tgt_174-168635-0000.wav",

      // XVC
      xvc_seen2seen: [
      { no: 1, 
          source: "./xvc-seen2seen/src_p237_010.wav", 
          neuralxvc: "./xvc-seen2seen/p237_010-p236_003.wav" ,
          bl: "./xvc-seen2seen/bl_p237_010-p236_003.wav"},
      { no: 2, 
          source: "./xvc-seen2seen/src_p239_012.wav", 
          neuralxvc: "./xvc-seen2seen/p239_012-p236_003.wav",
          bl: "./xvc-seen2seen/bl_p239_012-p236_003.wav" },
      { no: 3, 
          source: "./xvc-seen2seen/src_p243_005.wav", 
          neuralxvc: "./xvc-seen2seen/p243_005-p236_003.wav",
          bl: "./xvc-seen2seen/bl_p243_005-p236_003.wav" },
      { no: 4, 
          source: "./xvc-seen2seen/src_p249_016.wav", 
          neuralxvc: "./xvc-seen2seen/p249_016-p236_003.wav",
          bl: "./xvc-seen2seen/bl_p249_016-p236_003.wav" },
      { no: 5, 
          source: "./xvc-seen2seen/src_p255_003.wav", 
          neuralxvc: "./xvc-seen2seen/p255_003-p236_003.wav",
          bl: "./xvc-seen2seen/bl_p255_003-p236_003.wav" },
        // Add more data as needed
      ],
      tgt4: "./xvc-seen2seen/tgt_p236_003.wav",

      xvc_unseen2seen: [
      { no: 1, 
          source: "./xvc-unseen2seen/src_174-168635-0000.wav", 
          neuralxvc: "./xvc-unseen2seen/174-168635-0000-p241_002.wav",
          bl: "./xvc-unseen2seen/bl_174-168635-0000-p241_002.wav" },
      { no: 2, 
          source: "./xvc-unseen2seen/src_2412-153948-0003.wav", 
          neuralxvc: "./xvc-unseen2seen/2412-153948-0003-p241_002.wav",
          bl: "./xvc-unseen2seen/bl_2412-153948-0003-p241_002.wav" },
      { no: 3, 
          source: "./xvc-unseen2seen/src_3536-23268-0015.wav", 
          neuralxvc: "./xvc-unseen2seen/3536-23268-0015-p241_002.wav",
          bl: "./xvc-unseen2seen/bl_3536-23268-0015-p241_002.wav" },
      { no: 4, 
          source: "./xvc-unseen2seen/src_5694-64038-0004.wav", 
          neuralxvc: "./xvc-unseen2seen/5694-64038-0004-p241_002.wav",
          bl: "./xvc-unseen2seen/bl_5694-64038-0004-p241_002.wav" },
      { no: 5, 
          source: "./xvc-unseen2seen/src_6319-57405-0012.wav", 
          neuralxvc: "./xvc-unseen2seen/6319-57405-0012-p241_002.wav",
          bl: "./xvc-unseen2seen/bl_6319-57405-0012-p241_002.wav" },
        // Add more data as needed
      ],
      tgt5: "./xvc-unseen2seen/tgt_p241_002.wav",

      xvc_unseen2unseen: [
      { no: 1, 
          source: "./xvc-unseen2unseen/src_84-121550-0008.wav", 
          neuralxvc: "./xvc-unseen2unseen/84-121550-0008-6295-244435-0000.wav",
          bl: "./xvc-unseen2unseen/bl_84-121550-0008-6295-244435-0000.wav" },
      { no: 2, 
          source: "./xvc-unseen2unseen/src_251-136532-0003.wav", 
          neuralxvc: "./xvc-unseen2unseen/251-136532-0003-6295-244435-0000.wav",
          bl: "./xvc-unseen2unseen/bl_251-136532-0003-6295-244435-0000.wav" },
      { no: 3, 
          source: "./xvc-unseen2unseen/src_777-126732-0018.wav", 
          neuralxvc: "./xvc-unseen2unseen/777-126732-0018-6295-244435-0000.wav",
          bl: "./xvc-unseen2unseen/bl_777-126732-0018-6295-244435-0000.wav" },
      { no: 4, 
          source: "./xvc-unseen2unseen/src_1462-170145-0006.wav", 
          neuralxvc: "./xvc-unseen2unseen/1462-170145-0006-6295-244435-0000.wav",
          bl: "./xvc-unseen2unseen/bl_1462-170145-0006-6295-244435-0000.wav" },
      { no: 5, 
          source: "./xvc-unseen2unseen/src_5338-284437-0003.wav", 
          neuralxvc: "./xvc-unseen2unseen/5338-284437-0003-6295-244435-0000.wav",
          bl: "./xvc-unseen2unseen/bl_5338-284437-0003-6295-244435-0000.wav" },
        // Add more data as needed
      ],
      tgt6: "./xvc-unseen2unseen/tgt_6295-244435-0000.wav",

      xvc_esd: [
      { no: 1, 
          source: "./xvc-esd/src_126_003_0152.wav", 
          xvc: "./xvc-esd/126_003_0152-0005_000001.wav" ,
          nvc:"./xvc-esd/nvc_126_003_0152-0005_000001.wav",
          bl:"./xvc-esd/bl_126_003_0152-0005_000001.wav"},
      { no: 2, 
          source: "./xvc-esd/src_1993-147964-0006.wav", 
          xvc: "./xvc-esd/1993-147964-0006-0005_000001.wav",
          nvc: "./xvc-esd/nvc_1993-147964-0006-0005_000001.wav",
          bl: "./xvc-esd/bl_1993-147964-0006-0005_000001.wav" },
      { no: 3, 
          source: "./xvc-esd/src_BASIC5000_1356.wav", 
          xvc: "./xvc-esd/BASIC5000_1356-0005_000001.wav",
          nvc: "./xvc-esd/nvc_BASIC5000_1356-0005_000001.wav",
          bl: "./xvc-esd/bl_BASIC5000_1356-0005_000001.wav" }
      ],
      tgt7: "./xvc-esd/tgt_0005_000001.wav",

      xvc_jvs: [
      { no: 1, 
          source: "./xvc-jvs/src_0005_000001.wav", 
          xvc: "./xvc-jvs/0005_000001-BASIC5000_1356.wav" ,
          nvc:"./xvc-jvs/nvc_0005_000001-BASIC5000_1356.wav",
          bl:"./xvc-jvs/bl_0005_000001-BASIC5000_1356.wav"},
      { no: 2, 
          source: "./xvc-jvs/src_126_003_0152.wav", 
          xvc: "./xvc-jvs/126_003_0152-BASIC5000_1356.wav",
          nvc: "./xvc-jvs/nvc_126_003_0152-BASIC5000_1356.wav" ,
          bl: "./xvc-jvs/bl_126_003_0152-BASIC5000_1356.wav" },
      { no: 3, 
          source: "./xvc-jvs/src_1993-147964-0006.wav", 
          xvc: "./xvc-jvs/1993-147964-0006-BASIC5000_1356.wav",
          nvc: "./xvc-jvs/nvc_1993-147964-0006-BASIC5000_1356.wav",
          bl: "./xvc-jvs/bl_1993-147964-0006-BASIC5000_1356.wav" }
      ],
      tgt8: "./xvc-jvs/tgt_BASIC5000_1356.wav",

      xvc_libritts: [
      { no: 1, 
          source: "./xvc-libritts/src_0005_000001.wav", 
          xvc: "./xvc-libritts/0005_000001-1993-147964-0006.wav" ,
          nvc:"./xvc-libritts/nvc_0005_000001-1993-147964-0006.wav",
          bl:"./xvc-libritts/bl_0005_000001-1993-147964-0006.wav"},
      { no: 2, 
          source: "./xvc-libritts/src_126_003_0152.wav", 
          xvc: "./xvc-libritts/126_003_0152-1993-147964-0006.wav",
          nvc: "./xvc-libritts/nvc_126_003_0152-1993-147964-0006.wav",
          bl: "./xvc-libritts/bl_126_003_0152-1993-147964-0006.wav" },
      { no: 3, 
          source: "./xvc-libritts/src_BASIC5000_1356.wav", 
          xvc: "./xvc-libritts/BASIC5000_1356-1993-147964-0006.wav",
          nvc: "./xvc-libritts/nvc_BASIC5000_1356-1993-147964-0006.wav",
          bl: "./xvc-libritts/bl_BASIC5000_1356-1993-147964-0006.wav" }
      ],
      tgt9: "./xvc-libritts/tgt_1993-147964-0006.wav",

      xvc_zeroth: [
      { no: 1, 
          source: "./xvc-zeroth/src_0005_000001.wav", 
          xvc: "./xvc-zeroth/0005_000001-126_003_0152.wav" ,
          nvc:"./xvc-zeroth/nvc_0005_000001-126_003_0152.wav",
          bl:"./xvc-zeroth/bl_0005_000001-126_003_0152.wav"},
      { no: 2, 
          source: "./xvc-zeroth/src_1993-147964-0006.wav", 
          xvc: "./xvc-zeroth/1993-147964-0006-126_003_0152.wav",
          nvc: "./xvc-zeroth/nvc_1993-147964-0006-126_003_0152.wav",
          bl: "./xvc-zeroth/bl_1993-147964-0006-126_003_0152.wav" },
      { no: 3, 
          source: "./xvc-zeroth/src_BASIC5000_1356.wav", 
          xvc: "./xvc-zeroth/BASIC5000_1356-126_003_0152.wav",
          nvc: "./xvc-zeroth/nvc_BASIC5000_1356-126_003_0152.wav",
          bl: "./xvc-zeroth/bl_BASIC5000_1356-126_003_0152.wav" }
      ],
      tgt10: "./xvc-zeroth/tgt_126_003_0152.wav",

      xvc_zeroth_same: [
      { no: 1, 
          source: "./xvc-zeroth-same/src_104_003_0437.wav", 
          xvc: "./xvc-zeroth-same/104_003_0437-137_003_0202.wav" ,
          nvc:"./xvc-zeroth-same/nvc_104_003_0437-137_003_0202.wav",
          bl:"./xvc-zeroth-same/bl_104_003_0437-137_003_0202.wav"},
      { no: 2, 
          source: "./xvc-zeroth-same/src_105_003_0029.wav", 
          xvc: "./xvc-zeroth-same/105_003_0029-137_003_0202.wav",
          nvc: "./xvc-zeroth-same/nvc_105_003_0029-137_003_0202.wav",
          bl: "./xvc-zeroth-same/bl_105_003_0029-137_003_0202.wav" },
      { no: 3, 
          source: "./xvc-zeroth-same/src_112_003_0932.wav", 
          xvc: "./xvc-zeroth-same/112_003_0932-137_003_0202.wav",
          nvc: "./xvc-zeroth-same/nvc_112_003_0932-137_003_0202.wav",
          bl: "./xvc-zeroth-same/bl_112_003_0932-137_003_0202.wav" },
      { no: 4, 
          source: "./xvc-zeroth-same/src_126_003_0152.wav", 
          xvc: "./xvc-zeroth-same/126_003_0152-137_003_0202.wav",
          nvc: "./xvc-zeroth-same/nvc_126_003_0152-137_003_0202.wav",
          bl: "./xvc-zeroth-same/bl_126_003_0152-137_003_0202.wav" }
      ],
      tgt11: "./xvc-zeroth-same/tgt_137_003_0202.wav",

      xvc_jvs_same: [
      { no: 1, 
          source: "./xvc-jvs-same/src_BASIC5000_0724.wav", 
          xvc: "./xvc-jvs-same/BASIC5000_0724-VOICEACTRESS100_003.wav" ,
          nvc:"./xvc-jvs-same/nvc_BASIC5000_0724-VOICEACTRESS100_003.wav",
          bl:"./xvc-jvs-same/bl_BASIC5000_0724-VOICEACTRESS100_003.wav"},
      { no: 2, 
          source: "./xvc-jvs-same/src_BASIC5000_1356.wav", 
          xvc: "./xvc-jvs-same/BASIC5000_1356-VOICEACTRESS100_003.wav",
          nvc: "./xvc-jvs-same/nvc_BASIC5000_1356-VOICEACTRESS100_003.wav",
          bl: "./xvc-jvs-same/bl_BASIC5000_1356-VOICEACTRESS100_003.wav" },
      { no: 3, 
          source: "./xvc-jvs-same/src_VOICEACTRESS100_005.wav", 
          xvc: "./xvc-jvs-same/VOICEACTRESS100_005-VOICEACTRESS100_003.wav",
          nvc: "./xvc-jvs-same/nvc_VOICEACTRESS100_005-VOICEACTRESS100_003.wav",
          bl: "./xvc-jvs-same/bl_VOICEACTRESS100_005-VOICEACTRESS100_003.wav" },
      { no: 4, 
          source: "./xvc-jvs-same/src_VOICEACTRESS100_008.wav", 
          xvc: "./xvc-jvs-same/VOICEACTRESS100_008-VOICEACTRESS100_003.wav",
          nvc: "./xvc-jvs-same/nvc_VOICEACTRESS100_008-VOICEACTRESS100_003.wav",
          bl: "./xvc-jvs-same/bl_VOICEACTRESS100_008-VOICEACTRESS100_003.wav" }
      ],
      tgt12: "./xvc-jvs-same/tgt_VOICEACTRESS100_003.wav",

      xvc_esd_same: [
      { no: 1, 
          source: "./xvc-esd-same/src_0004_000011.wav", 
          xvc: "./xvc-esd-same/0004_000011-0001_000002.wav" ,
          nvc:"./xvc-esd-same/ncv_0004_000011-0001_000002.wav",
          bl:"./xvc-esd-same/bl_0004_000011-0001_000002.wav"},
      { no: 2, 
          source: "./xvc-esd-same/src_0006_000025.wav", 
          xvc: "./xvc-esd-same/0006_000025-0001_000002.wav",
          nvc: "./xvc-esd-same/ncv_0006_000025-0001_000002.wav",
          bl: "./xvc-esd-same/bl_0006_000025-0001_000002.wav" },
      { no: 3, 
          source: "./xvc-esd-same/src_0007_000004.wav", 
          xvc: "./xvc-esd-same/0007_000004-0001_000002.wav",
          nvc: "./xvc-esd-same/ncv_0007_000004-0001_000002.wav",
          bl: "./xvc-esd-same/bl_0007_000004-0001_000002.wav" },
      { no: 4, 
          source: "./xvc-esd-same/src_0008_000014.wav", 
          xvc: "./xvc-esd-same/0008_000014-0001_000002.wav",
          nvc: "./xvc-esd-same/ncv_0008_000014-0001_000002.wav",
          bl: "./xvc-esd-same/bl_0008_000014-0001_000002.wav" }
      ],
      tgt13: "./xvc-esd-same/tgt_0001_000002.wav",

      evc_angry: [
      { no: 1, 
          source: "./evc-angry/src_0017_000713.wav", 
          evc: "./evc-angry/0017_000713-0015_000377.wav" ,
          nvc:"./evc-angry/nvc_0017_000713-0015_000377.wav"},
      { no: 2, 
          source: "./evc-angry/src_0019_000002.wav", 
          evc: "./evc-angry/0019_000002-0015_000377.wav",
          nvc: "./evc-angry/nvc_0019_000002-0015_000377.wav" },
      { no: 3, 
          source: "./evc-angry/src_0020_001057.wav", 
          evc: "./evc-angry/0020_001057-0015_000377.wav",
          nvc: "./evc-angry/nvc_0020_001057-0015_000377.wav" },
      { no: 4, 
          source: "./evc-angry/src_0020_001417.wav", 
          evc: "./evc-angry/0020_001417-0015_000377.wav",
          nvc: "./evc-angry/nvc_0020_001417-0015_000377.wav" }
      ],
      tgt14: "./evc-angry/tgt_0015_000377.wav",

      evc_happy: [
      { no: 1, 
          source: "./evc-happy/src_0015_000377.wav", 
          evc: "./evc-happy/0015_000377-0017_000713.wav" ,
          nvc:"./evc-happy/nvc_0015_000377-0017_000713.wav"},
      { no: 2, 
          source: "./evc-happy/src_0019_000002.wav", 
          evc: "./evc-happy/0019_000002-0017_000713.wav",
          nvc: "./evc-happy/nvc_0019_000002-0017_000713.wav" },
      { no: 3, 
          source: "./evc-happy/src_0020_001057.wav", 
          evc: "./evc-happy/0020_001057-0017_000713.wav",
          nvc: "./evc-happy/nvc_0020_001057-0017_000713.wav" },
      { no: 4, 
          source: "./evc-happy/src_0020_001417.wav", 
          evc: "./evc-happy/0020_001417-0017_000713.wav",
          nvc: "./evc-happy/nvc_0020_001417-0017_000713.wav" }
      ],
      tgt15: "./evc-happy/tgt_0017_000713.wav",

      evc_neutral: [
      { no: 1, 
          source: "./evc-neutral/src_0015_000377.wav", 
          evc: "./evc-neutral/0015_000377-0019_000002.wav" ,
          nvc:"./evc-neutral/nvc_0015_000377-0019_000002.wav"},
      { no: 2, 
          source: "./evc-neutral/src_0017_000713.wav", 
          evc: "./evc-neutral/0017_000713-0019_000002.wav",
          nvc: "./evc-neutral/nvc_0017_000713-0019_000002.wav" },
      { no: 3, 
          source: "./evc-neutral/src_0020_001057.wav", 
          evc: "./evc-neutral/0020_001057-0019_000002.wav",
          nvc: "./evc-neutral/nvc_0020_001057-0019_000002.wav" },
      { no: 4, 
          source: "./evc-neutral/src_0020_001417.wav", 
          evc: "./evc-neutral/0020_001417-0019_000002.wav",
          nvc: "./evc-neutral/nvc_0020_001417-0019_000002.wav" }
      ],
      tgt16: "./evc-neutral/tgt_0019_000002.wav",


      evc_sad: [
      { no: 1, 
          source: "./evc-sad/src_0015_000377.wav", 
          evc: "./evc-sad/0015_000377-0020_001057.wav" ,
          nvc:"./evc-sad/nvc_0015_000377-0020_001057.wav"},
      { no: 2, 
          source: "./evc-sad/src_0017_000713.wav", 
          evc: "./evc-sad/0017_000713-0020_001057.wav",
          nvc: "./evc-sad/nvc_0017_000713-0020_001057.wav" },
      { no: 3, 
          source: "./evc-sad/src_0019_000002.wav", 
          evc: "./evc-sad/0019_000002-0020_001057.wav",
          nvc: "./evc-sad/nvc_0019_000002-0020_001057.wav" },
      { no: 4, 
          source: "./evc-sad/src_0020_001417.wav", 
          evc: "./evc-sad/0020_001417-0020_001057.wav",
          nvc: "./evc-sad/nvc_0020_001417-0020_001057.wav" }
      ],
      tgt17: "./evc-sad/tgt_0020_001057.wav",

      evc_emo_angry: [
      { no: 1, 
          source: "./evc-emo-angry/src_amused_1-15_0001.wav", 
          evc: "./evc-emo-angry/amused_1-15_0001-anger_1-28_0002.wav" ,
          nvc:"./evc-emo-angry/nvc_amused_1-15_0001-anger_1-28_0002.wav"},
      { no: 2, 
          source: "./evc-emo-angry/src_disgust_29-56_0030.wav", 
          evc: "./evc-emo-angry/disgust_29-56_0030-anger_1-28_0002.wav",
          nvc: "./evc-emo-angry/nvc_disgust_29-56_0030-anger_1-28_0002.wav" },
      { no: 3, 
          source: "./evc-emo-angry/src_amused_1-15_0001.wav", 
          evc: "./evc-emo-angry/Neutral_1-28_0001-anger_1-28_0002.wav",
          nvc: "./evc-emo-angry/nvc_Neutral_1-28_0001-anger_1-28_0002.wav" }
      ],
      tgt18: "./evc-emo-angry/tgt_anger_1-28_0002.wav",

      evc_emo_disgust: [
      { no: 1, 
          source: "./evc-emo-disgust/src_amused_1-15_0001.wav", 
          evc: "./evc-emo-disgust/amused_1-15_0001-disgust_29-56_0030.wav" ,
          nvc:"./evc-emo-disgust/nvc_amused_1-15_0001-disgust_29-56_0030.wav"},
      { no: 2, 
          source: "./evc-emo-disgust/src_anger_1-28_0002.wav", 
          evc: "./evc-emo-disgust/anger_1-28_0002-disgust_29-56_0030.wav",
          nvc: "./evc-emo-disgust/nvc_anger_1-28_0002-disgust_29-56_0030.wav" },
      { no: 3, 
          source: "./evc-emo-disgust/src_Neutral_1-28_0001.wav", 
          evc: "./evc-emo-disgust/Neutral_1-28_0001-disgust_29-56_0030.wav",
          nvc: "./evc-emo-disgust/nvc_Neutral_1-28_0001-disgust_29-56_0030.wav" }
      ],
      tgt19: "./evc-emo-disgust/tgt_disgust_29-56_0030.wav",

      evc_emo_happy: [
      { no: 1, 
          source: "./evc-emo-happy/src_anger_1-28_0002.wav", 
          evc: "./evc-emo-happy/anger_1-28_0002-amused_1-15_0001.wav" ,
          nvc:"./evc-emo-happy/nvc_anger_1-28_0002-amused_1-15_0001.wav"},
      { no: 2, 
          source: "./evc-emo-happy/src_disgust_29-56_0030.wav", 
          evc: "./evc-emo-happy/disgust_29-56_0030-amused_1-15_0001.wav",
          nvc: "./evc-emo-happy/nvc_disgust_29-56_0030-amused_1-15_0001.wav" },
      { no: 3, 
          source: "./evc-emo-happy/src_Neutral_1-28_0001.wav", 
          evc: "./evc-emo-happy/Neutral_1-28_0001-amused_1-15_0001.wav",
          nvc: "./evc-emo-happy/nvc_Neutral_1-28_0001-amused_1-15_0001.wav" }
      ],
      tgt20: "./evc-emo-happy/tgt_amused_1-15_0001.wav",

      evc_emo_neutral: [
      { no: 1, 
          source: "./evc-emo-neutral/src_amused_1-15_0001.wav", 
          evc: "./evc-emo-neutral/amused_1-15_0001-Neutral_1-28_0001.wav" ,
          nvc:"./evc-emo-neutral/nvc_amused_1-15_0001-Neutral_1-28_0001.wav"},
      { no: 2, 
          source: "./evc-emo-neutral/src_anger_1-28_0002.wav", 
          evc: "./evc-emo-neutral/anger_1-28_0002-Neutral_1-28_0001.wav",
          nvc: "./evc-emo-neutral/nvc_anger_1-28_0002-Neutral_1-28_0001.wav" },
      { no: 3, 
          source: "./evc-emo-neutral/src_disgust_29-56_0030.wav", 
          evc: "./evc-emo-neutral/disgust_29-56_0030-Neutral_1-28_0001.wav",
          nvc: "./evc-emo-neutral/nvc_disgust_29-56_0030-Neutral_1-28_0001.wav" }
      ],
      tgt21: "./evc-emo-neutral/tgt_Neutral_1-28_0001.wav",

      
    };
  }
};
</script>


<style>
.container {
  max-height: 100vh; /* 100vh 表示视窗的100%，你可以根据需要调整 */
  overflow-y: auto; /* 当内容超出容器高度时显示滚动条 */
}


.audio-card {
  margin-bottom: 20px;
}

.h1-realtime{
  position: absolute;
  top: 15px;
  left: 20px;
}


.line1 {
  float: right;
  width: 100%; 
  height: 5px; 
  position: absolute;
  background-color: grey; 
  top: 1580px;
  left: 15px;
  right: 10px;
}

.line2 {
  float: right;
  width: 100%; 
  height: 5px; 
  position: absolute;
  background-color: grey; 
  top: 5880px;
  left: 15px;
  right: 10px;
}

.h2-realtime-seen2seen{
  position: absolute;
  top: 75px;
  left: 20px;
}

.realtime-display-seen2seen{
  position: absolute;
  top: 120px;
  left: 20px;
}

.h2-realtime-unseen2seen{
  position: absolute;
  top: 570px;
  left: 20px;
}

.realtime-display-unseen2seen{
  position: absolute;
  top: 630px;
  left: 20px;
}

.h3-realtime-unseen2unseen{
  position: absolute;
  top: 1080px;
  left: 20px;
}


.realtime-display-unseen2unseen{
  position: absolute;
  top: 1130px;
  left: 20px;
}

.h2-realtime{
  position: absolute;
  top: 1600px;
  left: 20px;
}

.xvc-display-seen2seen{
  position: absolute;
  top: 1730px;
  left: 20px;
}


.xvc-title-seen2seen{
  position: absolute;
  top: 1670px;
  left: 20px;
}

.xvc-display-unseen2seen{
  position: absolute;
  top: 2250px;
  left: 20px;
}


.xvc-title-unseen2seen{
  position: absolute;
  top: 2200px;
  left: 20px;
}

.xvc-title-unseen2unseen{
  position: absolute;
  top: 2700px;
  left: 20px;
}

.xvc-display-unseen2unseen{
  position: absolute;
  top: 2750px;
  left: 20px;
}

.xvc-title-esd{
  position: absolute;
  top: 3200px;
  left: 20px;
}

.xvc-display-esd{
  position: absolute;
  top: 3250px;
  left: 20px;
}

.xvc-title-jvs{
  position: absolute;
  top: 3550px;
  left: 20px;
}

.xvc-display-jvs{
  position: absolute;
  top: 3600px;
  left: 20px;
}

.xvc-title-libritts{
  position: absolute;
  top: 3900px;
  left: 20px;
}

.xvc-display-libritts{
  position: absolute;
  top: 3950px;
  left: 20px;
}

.xvc-title-zeroth{
  position: absolute;
  top: 4250px;
  left: 20px;
}

.xvc-display-zeroth{
  position: absolute;
  top: 4300px;
  left: 20px;
}

.xvc-title-zeroth-same{
  position: absolute;
  top: 4600px;
  left: 20px;
}

.xvc-display-zeroth-same{
  position: absolute;
  top: 4650px;
  left: 20px;
}


.xvc-title-jvs-same{
  position: absolute;
  top: 5050px;
  left: 20px;
}

.xvc-display-jvs-same{
  position: absolute;
  top: 5100px;
  left: 20px;
}

.xvc-title-esd-same{
  position: absolute;
  top: 5480px;
  left: 20px;
}

.xvc-display-esd-same{
  position: absolute;
  top: 5530px;
  left: 20px;
}

.h3-evc{
  position: absolute;
  top: 5900px;
  left: 20px;
}


.evc-title-evc-angry{
  position: absolute;
  top: 5980px;
  left: 20px;
}

.evc-display-evc-angry{
  position: absolute;
  top: 6050px;
  left: 20px;
}


.evc-title-evc-happy{
  position: absolute;
  top: 6420px;
  left: 20px;
}

.evc-display-evc-happy{
  position: absolute;
  top: 6480px;
  left: 20px;
}


.evc-title-evc-neutral{
  position: absolute;
  top: 6850px;
  left: 20px;
}

.evc-display-evc-neutral{
  position: absolute;
  top: 6900px;
  left: 20px;
}

.evc-title-evc-sad{
  position: absolute;
  top: 7280px;
  left: 20px;
}

.evc-display-evc-sad{
  position: absolute;
  top: 7340px;
  left: 20px;
}

.evc-title-emo-angry{
  position: absolute;
  top: 7720px;
  left: 20px;
}

.evc-display-emo-angry{
  position: absolute;
  top: 7780px;
  left: 20px;
}

.evc-title-emo-disgust{
  position: absolute;
  top: 8080px;
  left: 20px;
}

.evc-display-emo-disgust{
  position: absolute;
  top: 8140px;
  left: 20px;
}

.evc-title-emo-happy{
  position: absolute;
  top: 8430px;
  left: 20px;
}

.evc-display-emo-happy{
  position: absolute;
  top: 8500px;
  left: 20px;
}

.evc-title-emo-neutral{
  position: absolute;
  top: 8790px;
  left: 20px;
}

.evc-display-emo-neutral{
  position: absolute;
  top: 8840px;
  left: 20px;
}


</style>
