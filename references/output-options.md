# 修订标红与打印版配置

## 配置来源

按用户当前明确要求、论文已有配置、以下默认值的顺序解析。已有约定可能写在 checklist、构建脚本或项目说明中，不要求改用新文件。缺少配置且需要持久化时，可将以下配置写入当前论文目录的 `PAPER_REVIEW_CONFIG.yaml`。该文件是供执行者读取的约定，不是现成的自动导出程序。

```yaml
revision:
  mark_changes: false
  color: red
  baseline: null
print:
  enabled: false
  remove_revision_marks: true
  remove_review_line_numbers: true
  remove_link_borders: true
  scale_whole_page: false
  scale_factor: null
  preserve_line_breaks: true
  preserve_pagination: true
  preserve_figure_colors: true
```

`baseline` 指定本轮比较的文件、版本或提交；空值时使用本轮修改前的稿件作为依据。`scale_factor` 为空时不套用固定倍率，仅在启用整页放大后，根据页面内容边界确定不会裁切的倍率。

## 修订标红

开启 `mark_changes` 时，沿用文档现有标记机制，仅标记本轮新增或修改的文字，未改内容和既有修订标记保持原样。不要把整段无关文字或整张图染红。关闭表示本轮不新增标红，不表示清除历史标记。

基线不明确且用户要求标记历史修改时，先确认比较版本；不能把无法判定的差异当作本轮修改。删除内容按已有修订机制处理，不为显示红色而将已删正文保留在正文中。

## 打印版

只有 `print.enabled` 开启或用户明确要求时才额外导出。输出为独立文件，保留修订版及源稿。根据配置分别移除修订色、审稿行号和链接边框；只处理修订颜色，不全局删除有语义的正文或图中颜色。

默认保持正文断行、分页和图色。若通过重编译移除标记或行号，必须核对版式是否变化，不能假定重编译必然保留布局。启用整页等比放大时，在页面层面处理，不通过更改字号、栏宽或正文边距重排文本，并确认没有裁切页码、图表或正文。

导出后核对页数、断行、分页、内容边界、图色以及要求移除的元素。工具无法满足配置时说明具体限制和待完成项，不把不符合要求的版本称为完成版。
