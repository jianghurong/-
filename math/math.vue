<template>
  <div>
    <div>
      <p class="tips">
        点击
        <img src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAABAAAAAQCAYAAAAf8/9hAAAABHNCSVQICAgIfAhkiAAAAAlwSFlzAAAN1wAADdcBQiibeAAAABl0RVh0U29mdHdhcmUAd3d3Lmlua3NjYXBlLm9yZ5vuPBoAAAEUSURBVDiNxY+xSgNBFEXPG7KEBW38Ab8gzU61naQSQbAR/Atb7QRRSeMfWKYxFkoKG60UtnDzEG1stbOxNCQL+6wWliU7BiycaoZ77+EM/PeRtsB73wPGwHpLZQocuwD8MDAGiIGDhQZpmsbz+fwTWA0AAIYd7/0OsA+MJ5PJOcBsNtsUkWpcAH0zmzbG36r61gEugDVgI0mSJ1V9EJHdqiUi93meP7YpOOCjVj5K0zQGtmudUegPzszOau9+URSnwEqlH0XRdQgggPPePwO9Zmhmt6q6FTQASjM7acmD+hUAVR0BL42s6Ha7N0sBFlmY2V2WZV/LAlDVK+C1ll3+Ngbo1O5lWZZ7zrmBiLwDw2UAfz4/dNtaTXH2UcAAAAAASUVORK5CYII=" />
        符号编辑数学公式
        点击
         <img src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAABAAAAAQCAYAAAAf8/9hAAAABHNCSVQICAgIfAhkiAAAAAlwSFlzAAAN1wAADdcBQiibeAAAABl0RVh0U29mdHdhcmUAd3d3Lmlua3NjYXBlLm9yZ5vuPBoAAAGPSURBVDiN1ZKxa1NRFMZ/5yY1COYPKFiEiNpBHe55SQiZdFBEHAQHQZwchapLodClCEKhi4Pg6KaSzamCQnDJEMiTDqIoGXTRRcHFR+K7x8G8cHkNdfabDt8558flu0c4QM1mc8XMboUQPo5Go6dAKM/IosVOp3N4MpmsAZvAkZn9NoRwJ03TNwcCkiS5ZmY7wLEFbDOz55VK5d5wOPwKUC06rVbrZJ7nj83sXGnpM7AMLAEiItdDCKeBMwCumMrz/AUQL/80s/Usy04AZ0VkN+qtFLvVyDwV1U+ccxvFM4H3wCVVvQxcdc49YxboPANVtaJuNBrVXq+XL8hgn9y/R/5LwHg8vquqS2VfVY+r6lqSJPPAY8C3qN4B9rz3FwG63W7de78NvAMemtkrZh8wB4QQbgBfIsiqiOyq6sssyz6IyDpwaNar7AOkafoaWAXuA78i0AX+XmKhPTO7QvkOYrXb7aPT6fSBiNyM7B/AVr1ef9Tv938X5kJAIe/9eefc7RDCp1qttj0YDL6XZ/4A/MWDnkkEniQAAAAASUVORK5CYII=" />
        符号编辑化学公式
      </p>
      <div class="toolbar" ref="toolbar"></div>
    </div>
    <div class="htmlEditor" ref="htmlEditor" contenteditable="true"></div>
    <div>
      <span>1.编辑公式</span>
    </div>
    <div>
      <span>2.</span>
      <button @click="renderMathML($refs.htmlEditor)">转MathML</button>
      <span>{{ mathML }}</span>
    </div>
    <div>
      <span>3.</span>
      <button @click="renderHTML(mathML)">转HTML</button>
      <span v-html="html"></span>
    </div>
  </div>
</template>

<script>
import '@wiris/mathtype-generic/wirisplugin-generic'

export default {
  data() {
    return {
      mathML: '',
      html: ''
    }
  },
  created() {
    this.init()
  },
  methods: {
    // 初始化编辑器
    init() {
      /*eslint-disable*/
      this.$nextTick(() => {
        this.genericIntegrationProperties = {};
        this.genericIntegrationProperties.target = this.$refs.htmlEditor;
        this.genericIntegrationProperties.toolbar = this.$refs.toolbar;
        this.genericIntegrationInstance = new WirisPlugin.GenericIntegration(this.genericIntegrationProperties);
        this.genericIntegrationInstance.init();
        this.genericIntegrationInstance.listeners.fire('onTargetReady', {});
      })
    },
    // 渲染mathML数据
    renderMathML(dom) {
      this.$nextTick(() => {
        this.mathML = this.getMathML(dom)
      })
    },
    // 渲染html数据
    renderHTML(mathml) {
      this.$nextTick(() => {
        this.html = this.getHTML(mathml)
      })
    },
    // 根据指定dom的元素的值获取对应的mathML格式数据
    getMathML(dom) {
      if (typeof dom === 'object' && typeof dom.innerHTML === 'string') {
        return WirisPlugin.Parser.endParse(dom.innerHTML)
      }
    },
    // 根据指定mathml数据生成html标签
    getHTML(mathml) {
      if (typeof mathml === 'string') {
        return WirisPlugin.Parser.initParse(mathml)
      }
    }
  }
}
</script>

<style lang="scss" scoped>
.tips {
  color: lightcoral;
}
.htmlEditor {
  width: 100%;
  height: 200px;
}
</style>