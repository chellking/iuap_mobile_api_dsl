# $badge
$badge是提供标记显示、隐藏的服务对象

## $badge.showBadge()
$badge.showBadge()该方法用来显示标记

**语法**```$badge.showBadge(jsonArgs)```

**参数**+ **target**：要显示角标的目标控件的id+ **text**：角标显示的内容+ **position**：显示在target控件的位置 topright | topleft | bottomright | bottomleft+ **margin-top**：标记距离默认位置的上边距+ **margin-bottom**：标记距离默认位置的下边距+ **margin-right**：标记距离默认位置的右边距+ **margin-left**：标记距离默认位置的左边距+ **textsize**：标记字体大小+ **textcolor**：标记字体颜色+ **background**：气泡背景色+ **background-image**：气泡背景图+ **width**：气泡宽度+ **height**：气泡高度

**实例**```$badge.showBadge({ "target" : "image0", "text" : "1", "position" : "topright"});$badge.showBadge({ "target" : "image0", //要显示角标的目标控件的id "text" : "1", //角标显示的内容 "position" : "topleft", //显示在target控件的位置 topright | topleft | bottomright | bottomleft "width" : "35", "height" : "35", "background" : "#0000ff", "textsize" : "20", "textcolor" : "#000000", "margin-top" : "20"});```

## $badge.hideBadge()
$badge.hideBadge()该方法用来隐藏显示的标记

**语法**```$badge.hideBadge(jsonArgs)```

**参数**+ **target**：要显示角标的目标控件的id

**实例**```$badge.hideBadge({ "target" : "image1"});```


