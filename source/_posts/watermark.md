---
title: watermark
date: 2021-12-20 15:50:15
tags:
---
## 在util目录下创建watermark.js
      let watermark = {};

      let id = "set-customer-watermark-id";

      let setWatermark = (dom, str) => {
        if (document.getElementById(id) !== null) {
          dom
            ? dom.removeChild(document.getElementById(id))
            : document.body.removeChild(document.getElementById(id));
        }

        // 创建一个画布
        let can = document.createElement("canvas");
        can.width = 200;
        can.height = 200;

        // 设置画布样式
        let cans = can.getContext("2d");
        cans.rotate((-30 * Math.PI) / 180);
        cans.font = "15px Vedana";
        cans.fillStyle = "rgba(0,0,0,0.15)";
        cans.textAlign = "left";
        cans.textBaseline = "Middle";
        cans.fillText(str, 0, can.height);

        // 创建整体容器，设置样式
        let div = document.createElement("div");
        div.id = id;
        div.style.pointerEvents = "none";
        div.style.top = "0px";
        div.style.left = "-100px";
        div.style.position = "absolute";
        div.style.zIndex = "1000";
        div.style.width = document.documentElement.clientWidth + "px";
        div.style.height = document.documentElement.clientHeight + "px";
        div.style.background =
          "url(" + can.toDataURL("image/png") + ") left top repeat";

        dom ? dom.appendChild(div) : document.body.appendChild(div);
        return id;
      };

      // 设置水印
      watermark.set = (dom, str) => {
        let id = setWatermark(dom, str);
        setInterval(() => {
          if (document.getElementById(id) === null) {
            id = setWatermark(dom, str);
          }
        }, 500);
        window.onresize = () => {
          setWatermark(dom, str);
        };
      };

      // 清除水印
      watermark.remove = () => {
        if (document.getElementById(id) !== null) {
          document.getElementById(id).style.display = "none";
        }
      };

      export default watermark;
## 使用
      <template>
        <div class="home" id="water-mark-content">
          <HelloWorld msg="Welcome to Your Vue.js App" />
        </div>
      </template>

      <script>
      // @ is an alias to /src
      import HelloWorld from "@/components/HelloWorld.vue";
      import Watermark from "@/utils/lib/watermark";

      export default {
        name: "Home",
        components: {
          HelloWorld,
        },
        mounted() {
          this.setWatermark();
        },
        methods: {
          setWatermark() {
            const text = `lorretta-2021年9月7日15点37分`;
            Watermark.set(document.getElementById("water-mark-content"), text);
          },
        },
      };
      </script>