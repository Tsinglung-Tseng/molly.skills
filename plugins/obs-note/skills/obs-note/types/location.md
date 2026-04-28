# 地理位置笔记规范

适用条件：笔记类型为地点（`type: location` / `餐厅` / `景点`）。

## 1. 获取坐标

- 使用 `mcp_amap-maps_maps_text_search` 搜索地点。
- 找到对应的 POI 后，使用 `search_detail` 获取精确坐标 `location: "lng,lat"`。

## 2. 导航链接

必须提供三种地图的跳转链接：

- Apple Maps: `maps://?ll=lat,lng&q=地点名称`
- 高德地图: `https://uri.amap.com/marker?position=lng,lat&name=地点名称`
- 百度地图: `baidumap://map/marker?location=lat,lng&title=地点名称`

示例：`[📍 Apple](maps://...) | [🗺️ 高德](https://uri.amap.com/...) | [🅱️ 百度](baidumap://...)`

## 3. Frontmatter

必须包含 `location` 字段，**强制使用多行列表格式**：

```yaml
location:
  - lat (纬度)
  - lng (经度)
```

注意：Map View 插件要求纬度在前。

## 4. Map View 题图

在 `# 标题` 下方立即插入 `mapview` 代码块。`query` 字段推荐使用 `path:"文件名.md"`（不要带文件夹前缀，除非在子目录中）。

```mapview
{"name":"地点名称","mapZoom":14,"centerLat":MERGE_LAT,"centerLng":MERGE_LNG,"query":"path:\"[文件名].md\"","autoFit":true,"embeddedHeight":400}
```
