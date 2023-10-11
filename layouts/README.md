
# layouts 資料夾

default.vue 是 app.vue 的概念，一個 template，其他 pages 中的內容會塞到 layouts.vue 的 <slot /> 區域

pages 資料夾中的下層資料夾若要套用特定的 layouts，可以在 pages 下層資料夾中的 .vue 中使用 definePageMeta() 方法。
