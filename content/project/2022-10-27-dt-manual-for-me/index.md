---
title: DT 包子速查手册
author: yuanfan
date: 2022-10-27T21:05:36+0800
slug: dt-manual-for-me
categories:
  - R
tags:
  - R
draft: no
output:
  blogdown::html_page:
    toc: true
---

<script src="{{< blogdown/postref >}}index_files/htmlwidgets/htmlwidgets.js"></script>
<link href="{{< blogdown/postref >}}index_files/datatables-css/datatables-crosstalk.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/datatables-binding/datatables.js"></script>
<script src="{{< blogdown/postref >}}index_files/jquery/jquery-3.6.0.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/dt-core/css/jquery.dataTables.min.css" rel="stylesheet" />
<link href="{{< blogdown/postref >}}index_files/dt-core/css/jquery.dataTables.extra.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/dt-core/js/jquery.dataTables.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/crosstalk/css/crosstalk.min.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/crosstalk/js/crosstalk.min.js"></script>
<script src="{{< blogdown/postref >}}index_files/htmlwidgets/htmlwidgets.js"></script>
<link href="{{< blogdown/postref >}}index_files/datatables-css/datatables-crosstalk.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/datatables-binding/datatables.js"></script>
<script src="{{< blogdown/postref >}}index_files/jquery/jquery-3.6.0.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/dt-core/css/jquery.dataTables.min.css" rel="stylesheet" />
<link href="{{< blogdown/postref >}}index_files/dt-core/css/jquery.dataTables.extra.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/dt-core/js/jquery.dataTables.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/crosstalk/css/crosstalk.min.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/crosstalk/js/crosstalk.min.js"></script>
<script src="{{< blogdown/postref >}}index_files/htmlwidgets/htmlwidgets.js"></script>
<link href="{{< blogdown/postref >}}index_files/datatables-css/datatables-crosstalk.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/datatables-binding/datatables.js"></script>
<script src="{{< blogdown/postref >}}index_files/jquery/jquery-3.6.0.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/dt-core/css/jquery.dataTables.min.css" rel="stylesheet" />
<link href="{{< blogdown/postref >}}index_files/dt-core/css/jquery.dataTables.extra.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/dt-core/js/jquery.dataTables.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/crosstalk/css/crosstalk.min.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/crosstalk/js/crosstalk.min.js"></script>
<script src="{{< blogdown/postref >}}index_files/htmlwidgets/htmlwidgets.js"></script>
<link href="{{< blogdown/postref >}}index_files/datatables-css/datatables-crosstalk.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/datatables-binding/datatables.js"></script>
<script src="{{< blogdown/postref >}}index_files/jquery/jquery-3.6.0.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/dt-core/css/jquery.dataTables.min.css" rel="stylesheet" />
<link href="{{< blogdown/postref >}}index_files/dt-core/css/jquery.dataTables.extra.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/dt-core/js/jquery.dataTables.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/crosstalk/css/crosstalk.min.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/crosstalk/js/crosstalk.min.js"></script>
<script src="{{< blogdown/postref >}}index_files/htmlwidgets/htmlwidgets.js"></script>
<link href="{{< blogdown/postref >}}index_files/datatables-css/datatables-crosstalk.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/datatables-binding/datatables.js"></script>
<script src="{{< blogdown/postref >}}index_files/jquery/jquery-3.6.0.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/dt-core/css/jquery.dataTables.min.css" rel="stylesheet" />
<link href="{{< blogdown/postref >}}index_files/dt-core/css/jquery.dataTables.extra.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/dt-core/js/jquery.dataTables.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/crosstalk/css/crosstalk.min.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/crosstalk/js/crosstalk.min.js"></script>
<script src="{{< blogdown/postref >}}index_files/htmlwidgets/htmlwidgets.js"></script>
<link href="{{< blogdown/postref >}}index_files/datatables-css/datatables-crosstalk.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/datatables-binding/datatables.js"></script>
<script src="{{< blogdown/postref >}}index_files/jquery/jquery-3.6.0.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/dt-core/css/jquery.dataTables.min.css" rel="stylesheet" />
<link href="{{< blogdown/postref >}}index_files/dt-core/css/jquery.dataTables.extra.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/dt-core/js/jquery.dataTables.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/crosstalk/css/crosstalk.min.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/crosstalk/js/crosstalk.min.js"></script>
<script src="{{< blogdown/postref >}}index_files/htmlwidgets/htmlwidgets.js"></script>
<link href="{{< blogdown/postref >}}index_files/datatables-css/datatables-crosstalk.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/datatables-binding/datatables.js"></script>
<script src="{{< blogdown/postref >}}index_files/jquery/jquery-3.6.0.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/dt-core/css/jquery.dataTables.min.css" rel="stylesheet" />
<link href="{{< blogdown/postref >}}index_files/dt-core/css/jquery.dataTables.extra.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/dt-core/js/jquery.dataTables.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/crosstalk/css/crosstalk.min.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/crosstalk/js/crosstalk.min.js"></script>
<script src="{{< blogdown/postref >}}index_files/htmlwidgets/htmlwidgets.js"></script>
<link href="{{< blogdown/postref >}}index_files/datatables-css/datatables-crosstalk.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/datatables-binding/datatables.js"></script>
<script src="{{< blogdown/postref >}}index_files/jquery/jquery-3.6.0.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/dt-core/css/jquery.dataTables.min.css" rel="stylesheet" />
<link href="{{< blogdown/postref >}}index_files/dt-core/css/jquery.dataTables.extra.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/dt-core/js/jquery.dataTables.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/crosstalk/css/crosstalk.min.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/crosstalk/js/crosstalk.min.js"></script>
<script src="{{< blogdown/postref >}}index_files/htmlwidgets/htmlwidgets.js"></script>
<link href="{{< blogdown/postref >}}index_files/datatables-css/datatables-crosstalk.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/datatables-binding/datatables.js"></script>
<script src="{{< blogdown/postref >}}index_files/jquery/jquery-3.6.0.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/dt-core/css/jquery.dataTables.min.css" rel="stylesheet" />
<link href="{{< blogdown/postref >}}index_files/dt-core/css/jquery.dataTables.extra.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/dt-core/js/jquery.dataTables.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/crosstalk/css/crosstalk.min.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/crosstalk/js/crosstalk.min.js"></script>
<script src="{{< blogdown/postref >}}index_files/htmlwidgets/htmlwidgets.js"></script>
<link href="{{< blogdown/postref >}}index_files/datatables-css/datatables-crosstalk.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/datatables-binding/datatables.js"></script>
<script src="{{< blogdown/postref >}}index_files/jquery/jquery-3.6.0.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/dt-core/css/jquery.dataTables.min.css" rel="stylesheet" />
<link href="{{< blogdown/postref >}}index_files/dt-core/css/jquery.dataTables.extra.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/dt-core/js/jquery.dataTables.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/crosstalk/css/crosstalk.min.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/crosstalk/js/crosstalk.min.js"></script>
<script src="{{< blogdown/postref >}}index_files/htmlwidgets/htmlwidgets.js"></script>
<link href="{{< blogdown/postref >}}index_files/datatables-css/datatables-crosstalk.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/datatables-binding/datatables.js"></script>
<script src="{{< blogdown/postref >}}index_files/jquery/jquery-3.6.0.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/dt-core/css/jquery.dataTables.min.css" rel="stylesheet" />
<link href="{{< blogdown/postref >}}index_files/dt-core/css/jquery.dataTables.extra.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/dt-core/js/jquery.dataTables.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/crosstalk/css/crosstalk.min.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/crosstalk/js/crosstalk.min.js"></script>
<script src="{{< blogdown/postref >}}index_files/htmlwidgets/htmlwidgets.js"></script>
<link href="{{< blogdown/postref >}}index_files/datatables-css/datatables-crosstalk.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/datatables-binding/datatables.js"></script>
<script src="{{< blogdown/postref >}}index_files/jquery/jquery-3.6.0.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/dt-core/css/jquery.dataTables.min.css" rel="stylesheet" />
<link href="{{< blogdown/postref >}}index_files/dt-core/css/jquery.dataTables.extra.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/dt-core/js/jquery.dataTables.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/crosstalk/css/crosstalk.min.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/crosstalk/js/crosstalk.min.js"></script>
<script src="{{< blogdown/postref >}}index_files/htmlwidgets/htmlwidgets.js"></script>
<link href="{{< blogdown/postref >}}index_files/datatables-css/datatables-crosstalk.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/datatables-binding/datatables.js"></script>
<script src="{{< blogdown/postref >}}index_files/jquery/jquery-3.6.0.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/dt-core/css/jquery.dataTables.min.css" rel="stylesheet" />
<link href="{{< blogdown/postref >}}index_files/dt-core/css/jquery.dataTables.extra.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/dt-core/js/jquery.dataTables.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/crosstalk/css/crosstalk.min.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/crosstalk/js/crosstalk.min.js"></script>
<script src="{{< blogdown/postref >}}index_files/htmlwidgets/htmlwidgets.js"></script>
<link href="{{< blogdown/postref >}}index_files/datatables-css/datatables-crosstalk.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/datatables-binding/datatables.js"></script>
<script src="{{< blogdown/postref >}}index_files/jquery/jquery-3.6.0.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/dt-core/css/jquery.dataTables.min.css" rel="stylesheet" />
<link href="{{< blogdown/postref >}}index_files/dt-core/css/jquery.dataTables.extra.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/dt-core/js/jquery.dataTables.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/crosstalk/css/crosstalk.min.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/crosstalk/js/crosstalk.min.js"></script>
<script src="{{< blogdown/postref >}}index_files/htmlwidgets/htmlwidgets.js"></script>
<link href="{{< blogdown/postref >}}index_files/datatables-css/datatables-crosstalk.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/datatables-binding/datatables.js"></script>
<script src="{{< blogdown/postref >}}index_files/jquery/jquery-3.6.0.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/dt-core/css/jquery.dataTables.min.css" rel="stylesheet" />
<link href="{{< blogdown/postref >}}index_files/dt-core/css/jquery.dataTables.extra.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/dt-core/js/jquery.dataTables.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/crosstalk/css/crosstalk.min.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/crosstalk/js/crosstalk.min.js"></script>
<script src="{{< blogdown/postref >}}index_files/htmlwidgets/htmlwidgets.js"></script>
<link href="{{< blogdown/postref >}}index_files/datatables-css/datatables-crosstalk.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/datatables-binding/datatables.js"></script>
<script src="{{< blogdown/postref >}}index_files/jquery/jquery-3.6.0.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/dt-core/css/jquery.dataTables.min.css" rel="stylesheet" />
<link href="{{< blogdown/postref >}}index_files/dt-core/css/jquery.dataTables.extra.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/dt-core/js/jquery.dataTables.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/crosstalk/css/crosstalk.min.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/crosstalk/js/crosstalk.min.js"></script>
<script src="{{< blogdown/postref >}}index_files/htmlwidgets/htmlwidgets.js"></script>
<link href="{{< blogdown/postref >}}index_files/datatables-css/datatables-crosstalk.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/datatables-binding/datatables.js"></script>
<script src="{{< blogdown/postref >}}index_files/jquery/jquery-3.6.0.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/dt-core/css/jquery.dataTables.min.css" rel="stylesheet" />
<link href="{{< blogdown/postref >}}index_files/dt-core/css/jquery.dataTables.extra.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/dt-core/js/jquery.dataTables.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/crosstalk/css/crosstalk.min.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/crosstalk/js/crosstalk.min.js"></script>
<script src="{{< blogdown/postref >}}index_files/htmlwidgets/htmlwidgets.js"></script>
<link href="{{< blogdown/postref >}}index_files/datatables-css/datatables-crosstalk.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/datatables-binding/datatables.js"></script>
<script src="{{< blogdown/postref >}}index_files/jquery/jquery-3.6.0.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/dt-core/css/jquery.dataTables.min.css" rel="stylesheet" />
<link href="{{< blogdown/postref >}}index_files/dt-core/css/jquery.dataTables.extra.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/dt-core/js/jquery.dataTables.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/crosstalk/css/crosstalk.min.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/crosstalk/js/crosstalk.min.js"></script>
<script src="{{< blogdown/postref >}}index_files/htmlwidgets/htmlwidgets.js"></script>
<link href="{{< blogdown/postref >}}index_files/datatables-css/datatables-crosstalk.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/datatables-binding/datatables.js"></script>
<script src="{{< blogdown/postref >}}index_files/jquery/jquery-3.6.0.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/dt-core/css/jquery.dataTables.min.css" rel="stylesheet" />
<link href="{{< blogdown/postref >}}index_files/dt-core/css/jquery.dataTables.extra.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/dt-core/js/jquery.dataTables.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/crosstalk/css/crosstalk.min.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/crosstalk/js/crosstalk.min.js"></script>
<script src="{{< blogdown/postref >}}index_files/htmlwidgets/htmlwidgets.js"></script>
<link href="{{< blogdown/postref >}}index_files/datatables-css/datatables-crosstalk.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/datatables-binding/datatables.js"></script>
<script src="{{< blogdown/postref >}}index_files/jquery/jquery-3.6.0.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/dt-core/css/jquery.dataTables.min.css" rel="stylesheet" />
<link href="{{< blogdown/postref >}}index_files/dt-core/css/jquery.dataTables.extra.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/dt-core/js/jquery.dataTables.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/crosstalk/css/crosstalk.min.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/crosstalk/js/crosstalk.min.js"></script>
<script src="{{< blogdown/postref >}}index_files/htmlwidgets/htmlwidgets.js"></script>
<link href="{{< blogdown/postref >}}index_files/datatables-css/datatables-crosstalk.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/datatables-binding/datatables.js"></script>
<script src="{{< blogdown/postref >}}index_files/jquery/jquery-3.6.0.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/dt-core/css/jquery.dataTables.min.css" rel="stylesheet" />
<link href="{{< blogdown/postref >}}index_files/dt-core/css/jquery.dataTables.extra.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/dt-core/js/jquery.dataTables.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/crosstalk/css/crosstalk.min.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/crosstalk/js/crosstalk.min.js"></script>
<script src="{{< blogdown/postref >}}index_files/htmlwidgets/htmlwidgets.js"></script>
<link href="{{< blogdown/postref >}}index_files/datatables-css/datatables-crosstalk.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/datatables-binding/datatables.js"></script>
<script src="{{< blogdown/postref >}}index_files/jquery/jquery-3.6.0.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/dt-core/css/jquery.dataTables.min.css" rel="stylesheet" />
<link href="{{< blogdown/postref >}}index_files/dt-core/css/jquery.dataTables.extra.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/dt-core/js/jquery.dataTables.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/crosstalk/css/crosstalk.min.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/crosstalk/js/crosstalk.min.js"></script>
<script src="{{< blogdown/postref >}}index_files/htmlwidgets/htmlwidgets.js"></script>
<link href="{{< blogdown/postref >}}index_files/datatables-css/datatables-crosstalk.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/datatables-binding/datatables.js"></script>
<script src="{{< blogdown/postref >}}index_files/jquery/jquery-3.6.0.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/dt-core/css/jquery.dataTables.min.css" rel="stylesheet" />
<link href="{{< blogdown/postref >}}index_files/dt-core/css/jquery.dataTables.extra.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/dt-core/js/jquery.dataTables.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/crosstalk/css/crosstalk.min.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/crosstalk/js/crosstalk.min.js"></script>
<script src="{{< blogdown/postref >}}index_files/htmlwidgets/htmlwidgets.js"></script>
<link href="{{< blogdown/postref >}}index_files/datatables-css/datatables-crosstalk.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/datatables-binding/datatables.js"></script>
<script src="{{< blogdown/postref >}}index_files/jquery/jquery-3.6.0.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/dt-core/css/jquery.dataTables.min.css" rel="stylesheet" />
<link href="{{< blogdown/postref >}}index_files/dt-core/css/jquery.dataTables.extra.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/dt-core/js/jquery.dataTables.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/crosstalk/css/crosstalk.min.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/crosstalk/js/crosstalk.min.js"></script>
<script src="{{< blogdown/postref >}}index_files/htmlwidgets/htmlwidgets.js"></script>
<link href="{{< blogdown/postref >}}index_files/datatables-css/datatables-crosstalk.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/datatables-binding/datatables.js"></script>
<script src="{{< blogdown/postref >}}index_files/jquery/jquery-3.6.0.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/dt-core/css/jquery.dataTables.min.css" rel="stylesheet" />
<link href="{{< blogdown/postref >}}index_files/dt-core/css/jquery.dataTables.extra.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/dt-core/js/jquery.dataTables.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/crosstalk/css/crosstalk.min.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/crosstalk/js/crosstalk.min.js"></script>
<script src="{{< blogdown/postref >}}index_files/htmlwidgets/htmlwidgets.js"></script>
<link href="{{< blogdown/postref >}}index_files/datatables-css/datatables-crosstalk.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/datatables-binding/datatables.js"></script>
<script src="{{< blogdown/postref >}}index_files/jquery/jquery-3.6.0.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/dt-core/css/jquery.dataTables.min.css" rel="stylesheet" />
<link href="{{< blogdown/postref >}}index_files/dt-core/css/jquery.dataTables.extra.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/dt-core/js/jquery.dataTables.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/crosstalk/css/crosstalk.min.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/crosstalk/js/crosstalk.min.js"></script>
<script src="{{< blogdown/postref >}}index_files/htmlwidgets/htmlwidgets.js"></script>
<link href="{{< blogdown/postref >}}index_files/datatables-css/datatables-crosstalk.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/datatables-binding/datatables.js"></script>
<script src="{{< blogdown/postref >}}index_files/jquery/jquery-3.6.0.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/dt-core/css/jquery.dataTables.min.css" rel="stylesheet" />
<link href="{{< blogdown/postref >}}index_files/dt-core/css/jquery.dataTables.extra.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/dt-core/js/jquery.dataTables.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/crosstalk/css/crosstalk.min.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/crosstalk/js/crosstalk.min.js"></script>
<script src="{{< blogdown/postref >}}index_files/htmlwidgets/htmlwidgets.js"></script>
<link href="{{< blogdown/postref >}}index_files/datatables-css/datatables-crosstalk.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/datatables-binding/datatables.js"></script>
<script src="{{< blogdown/postref >}}index_files/jquery/jquery-3.6.0.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/dt-core/css/jquery.dataTables.min.css" rel="stylesheet" />
<link href="{{< blogdown/postref >}}index_files/dt-core/css/jquery.dataTables.extra.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/dt-core/js/jquery.dataTables.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/crosstalk/css/crosstalk.min.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/crosstalk/js/crosstalk.min.js"></script>
<script src="{{< blogdown/postref >}}index_files/htmlwidgets/htmlwidgets.js"></script>
<link href="{{< blogdown/postref >}}index_files/datatables-css/datatables-crosstalk.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/datatables-binding/datatables.js"></script>
<script src="{{< blogdown/postref >}}index_files/jquery/jquery-3.6.0.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/dt-core/css/jquery.dataTables.min.css" rel="stylesheet" />
<link href="{{< blogdown/postref >}}index_files/dt-core/css/jquery.dataTables.extra.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/dt-core/js/jquery.dataTables.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/crosstalk/css/crosstalk.min.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/crosstalk/js/crosstalk.min.js"></script>
<script src="{{< blogdown/postref >}}index_files/htmlwidgets/htmlwidgets.js"></script>
<link href="{{< blogdown/postref >}}index_files/datatables-css/datatables-crosstalk.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/datatables-binding/datatables.js"></script>
<script src="{{< blogdown/postref >}}index_files/jquery/jquery-3.6.0.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/dt-core/css/jquery.dataTables.min.css" rel="stylesheet" />
<link href="{{< blogdown/postref >}}index_files/dt-core/css/jquery.dataTables.extra.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/dt-core/js/jquery.dataTables.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/crosstalk/css/crosstalk.min.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/crosstalk/js/crosstalk.min.js"></script>
<script src="{{< blogdown/postref >}}index_files/htmlwidgets/htmlwidgets.js"></script>
<link href="{{< blogdown/postref >}}index_files/datatables-css/datatables-crosstalk.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/datatables-binding/datatables.js"></script>
<script src="{{< blogdown/postref >}}index_files/jquery/jquery-3.6.0.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/dt-core/css/jquery.dataTables.min.css" rel="stylesheet" />
<link href="{{< blogdown/postref >}}index_files/dt-core/css/jquery.dataTables.extra.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/dt-core/js/jquery.dataTables.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/crosstalk/css/crosstalk.min.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/crosstalk/js/crosstalk.min.js"></script>
<script src="{{< blogdown/postref >}}index_files/htmlwidgets/htmlwidgets.js"></script>
<link href="{{< blogdown/postref >}}index_files/datatables-css/datatables-crosstalk.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/datatables-binding/datatables.js"></script>
<script src="{{< blogdown/postref >}}index_files/jquery/jquery-3.6.0.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/dt-core/css/jquery.dataTables.min.css" rel="stylesheet" />
<link href="{{< blogdown/postref >}}index_files/dt-core/css/jquery.dataTables.extra.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/dt-core/js/jquery.dataTables.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/crosstalk/css/crosstalk.min.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/crosstalk/js/crosstalk.min.js"></script>
<script src="{{< blogdown/postref >}}index_files/htmlwidgets/htmlwidgets.js"></script>
<link href="{{< blogdown/postref >}}index_files/datatables-css/datatables-crosstalk.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/datatables-binding/datatables.js"></script>
<script src="{{< blogdown/postref >}}index_files/jquery/jquery-3.6.0.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/dt-core/css/jquery.dataTables.min.css" rel="stylesheet" />
<link href="{{< blogdown/postref >}}index_files/dt-core/css/jquery.dataTables.extra.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/dt-core/js/jquery.dataTables.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/crosstalk/css/crosstalk.min.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/crosstalk/js/crosstalk.min.js"></script>
<script src="{{< blogdown/postref >}}index_files/htmlwidgets/htmlwidgets.js"></script>
<link href="{{< blogdown/postref >}}index_files/datatables-css/datatables-crosstalk.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/datatables-binding/datatables.js"></script>
<script src="{{< blogdown/postref >}}index_files/jquery/jquery-3.6.0.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/dt-core/css/jquery.dataTables.min.css" rel="stylesheet" />
<link href="{{< blogdown/postref >}}index_files/dt-core/css/jquery.dataTables.extra.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/dt-core/js/jquery.dataTables.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/crosstalk/css/crosstalk.min.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/crosstalk/js/crosstalk.min.js"></script>
<script src="{{< blogdown/postref >}}index_files/htmlwidgets/htmlwidgets.js"></script>
<link href="{{< blogdown/postref >}}index_files/datatables-css/datatables-crosstalk.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/datatables-binding/datatables.js"></script>
<script src="{{< blogdown/postref >}}index_files/jquery/jquery-3.6.0.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/dt-core/css/jquery.dataTables.min.css" rel="stylesheet" />
<link href="{{< blogdown/postref >}}index_files/dt-core/css/jquery.dataTables.extra.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/dt-core/js/jquery.dataTables.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/crosstalk/css/crosstalk.min.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/crosstalk/js/crosstalk.min.js"></script>
<script src="{{< blogdown/postref >}}index_files/htmlwidgets/htmlwidgets.js"></script>
<link href="{{< blogdown/postref >}}index_files/datatables-css/datatables-crosstalk.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/datatables-binding/datatables.js"></script>
<script src="{{< blogdown/postref >}}index_files/jquery/jquery-3.6.0.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/dt-core/css/jquery.dataTables.min.css" rel="stylesheet" />
<link href="{{< blogdown/postref >}}index_files/dt-core/css/jquery.dataTables.extra.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/dt-core/js/jquery.dataTables.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/crosstalk/css/crosstalk.min.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/crosstalk/js/crosstalk.min.js"></script>
<script src="{{< blogdown/postref >}}index_files/htmlwidgets/htmlwidgets.js"></script>
<link href="{{< blogdown/postref >}}index_files/datatables-css/datatables-crosstalk.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/datatables-binding/datatables.js"></script>
<script src="{{< blogdown/postref >}}index_files/jquery/jquery-3.6.0.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/dt-core/css/jquery.dataTables.min.css" rel="stylesheet" />
<link href="{{< blogdown/postref >}}index_files/dt-core/css/jquery.dataTables.extra.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/dt-core/js/jquery.dataTables.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/dt-ext-fixedcolumns/css/fixedColumns.dataTables.min.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/dt-ext-fixedcolumns/js/dataTables.fixedColumns.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/crosstalk/css/crosstalk.min.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/crosstalk/js/crosstalk.min.js"></script>
<script src="{{< blogdown/postref >}}index_files/htmlwidgets/htmlwidgets.js"></script>
<link href="{{< blogdown/postref >}}index_files/datatables-css/datatables-crosstalk.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/datatables-binding/datatables.js"></script>
<script src="{{< blogdown/postref >}}index_files/jquery/jquery-3.6.0.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/dt-core/css/jquery.dataTables.min.css" rel="stylesheet" />
<link href="{{< blogdown/postref >}}index_files/dt-core/css/jquery.dataTables.extra.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/dt-core/js/jquery.dataTables.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/crosstalk/css/crosstalk.min.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/crosstalk/js/crosstalk.min.js"></script>
<script src="{{< blogdown/postref >}}index_files/htmlwidgets/htmlwidgets.js"></script>
<link href="{{< blogdown/postref >}}index_files/datatables-css/datatables-crosstalk.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/datatables-binding/datatables.js"></script>
<script src="{{< blogdown/postref >}}index_files/jquery/jquery-3.6.0.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/dt-core/css/jquery.dataTables.min.css" rel="stylesheet" />
<link href="{{< blogdown/postref >}}index_files/dt-core/css/jquery.dataTables.extra.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/dt-core/js/jquery.dataTables.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/crosstalk/css/crosstalk.min.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/crosstalk/js/crosstalk.min.js"></script>
<script src="{{< blogdown/postref >}}index_files/htmlwidgets/htmlwidgets.js"></script>
<link href="{{< blogdown/postref >}}index_files/datatables-css/datatables-crosstalk.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/datatables-binding/datatables.js"></script>
<script src="{{< blogdown/postref >}}index_files/jquery/jquery-3.6.0.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/dt-core/css/jquery.dataTables.min.css" rel="stylesheet" />
<link href="{{< blogdown/postref >}}index_files/dt-core/css/jquery.dataTables.extra.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/dt-core/js/jquery.dataTables.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/crosstalk/css/crosstalk.min.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/crosstalk/js/crosstalk.min.js"></script>
<script src="{{< blogdown/postref >}}index_files/htmlwidgets/htmlwidgets.js"></script>
<link href="{{< blogdown/postref >}}index_files/datatables-css/datatables-crosstalk.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/datatables-binding/datatables.js"></script>
<script src="{{< blogdown/postref >}}index_files/jquery/jquery-3.6.0.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/dt-core/css/jquery.dataTables.min.css" rel="stylesheet" />
<link href="{{< blogdown/postref >}}index_files/dt-core/css/jquery.dataTables.extra.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/dt-core/js/jquery.dataTables.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/crosstalk/css/crosstalk.min.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/crosstalk/js/crosstalk.min.js"></script>
<script src="{{< blogdown/postref >}}index_files/htmlwidgets/htmlwidgets.js"></script>
<link href="{{< blogdown/postref >}}index_files/datatables-css/datatables-crosstalk.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/datatables-binding/datatables.js"></script>
<script src="{{< blogdown/postref >}}index_files/jquery/jquery-3.6.0.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/dt-core/css/jquery.dataTables.min.css" rel="stylesheet" />
<link href="{{< blogdown/postref >}}index_files/dt-core/css/jquery.dataTables.extra.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/dt-core/js/jquery.dataTables.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/crosstalk/css/crosstalk.min.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/crosstalk/js/crosstalk.min.js"></script>
<script src="{{< blogdown/postref >}}index_files/htmlwidgets/htmlwidgets.js"></script>
<link href="{{< blogdown/postref >}}index_files/datatables-css/datatables-crosstalk.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/datatables-binding/datatables.js"></script>
<script src="{{< blogdown/postref >}}index_files/jquery/jquery-3.6.0.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/dt-core/css/jquery.dataTables.min.css" rel="stylesheet" />
<link href="{{< blogdown/postref >}}index_files/dt-core/css/jquery.dataTables.extra.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/dt-core/js/jquery.dataTables.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/crosstalk/css/crosstalk.min.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/crosstalk/js/crosstalk.min.js"></script>
<script src="{{< blogdown/postref >}}index_files/htmlwidgets/htmlwidgets.js"></script>
<link href="{{< blogdown/postref >}}index_files/datatables-css/datatables-crosstalk.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/datatables-binding/datatables.js"></script>
<script src="{{< blogdown/postref >}}index_files/jquery/jquery-3.6.0.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/dt-core/css/jquery.dataTables.min.css" rel="stylesheet" />
<link href="{{< blogdown/postref >}}index_files/dt-core/css/jquery.dataTables.extra.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/dt-core/js/jquery.dataTables.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/crosstalk/css/crosstalk.min.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/crosstalk/js/crosstalk.min.js"></script>
<script src="{{< blogdown/postref >}}index_files/htmlwidgets/htmlwidgets.js"></script>
<link href="{{< blogdown/postref >}}index_files/datatables-css/datatables-crosstalk.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/datatables-binding/datatables.js"></script>
<script src="{{< blogdown/postref >}}index_files/jquery/jquery-3.6.0.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/dt-core/css/jquery.dataTables.min.css" rel="stylesheet" />
<link href="{{< blogdown/postref >}}index_files/dt-core/css/jquery.dataTables.extra.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/dt-core/js/jquery.dataTables.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/crosstalk/css/crosstalk.min.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/crosstalk/js/crosstalk.min.js"></script>
<script src="{{< blogdown/postref >}}index_files/htmlwidgets/htmlwidgets.js"></script>
<link href="{{< blogdown/postref >}}index_files/datatables-css/datatables-crosstalk.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/datatables-binding/datatables.js"></script>
<script src="{{< blogdown/postref >}}index_files/jquery/jquery-3.6.0.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/dt-core/css/jquery.dataTables.min.css" rel="stylesheet" />
<link href="{{< blogdown/postref >}}index_files/dt-core/css/jquery.dataTables.extra.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/dt-core/js/jquery.dataTables.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/crosstalk/css/crosstalk.min.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/crosstalk/js/crosstalk.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/jquery-sparkline/jquery.sparkline.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/jquery-sparkline/jquery.sparkline.js"></script>
<script src="{{< blogdown/postref >}}index_files/sparkline-binding/sparkline.js"></script>
<script src="{{< blogdown/postref >}}index_files/htmlwidgets/htmlwidgets.js"></script>
<link href="{{< blogdown/postref >}}index_files/datatables-css/datatables-crosstalk.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/datatables-binding/datatables.js"></script>
<script src="{{< blogdown/postref >}}index_files/jquery/jquery-3.6.0.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/dt-core/css/jquery.dataTables.min.css" rel="stylesheet" />
<link href="{{< blogdown/postref >}}index_files/dt-core/css/jquery.dataTables.extra.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/dt-core/js/jquery.dataTables.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/crosstalk/css/crosstalk.min.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/crosstalk/js/crosstalk.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/jquery-sparkline/jquery.sparkline.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/jquery-sparkline/jquery.sparkline.js"></script>
<script src="{{< blogdown/postref >}}index_files/sparkline-binding/sparkline.js"></script>
<script src="{{< blogdown/postref >}}index_files/htmlwidgets/htmlwidgets.js"></script>
<link href="{{< blogdown/postref >}}index_files/datatables-css/datatables-crosstalk.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/datatables-binding/datatables.js"></script>
<script src="{{< blogdown/postref >}}index_files/jquery/jquery-3.6.0.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/dt-core/css/jquery.dataTables.min.css" rel="stylesheet" />
<link href="{{< blogdown/postref >}}index_files/dt-core/css/jquery.dataTables.extra.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/dt-core/js/jquery.dataTables.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/crosstalk/css/crosstalk.min.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/crosstalk/js/crosstalk.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/jquery-sparkline/jquery.sparkline.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/jquery-sparkline/jquery.sparkline.js"></script>
<script src="{{< blogdown/postref >}}index_files/sparkline-binding/sparkline.js"></script>
<script src="{{< blogdown/postref >}}index_files/htmlwidgets/htmlwidgets.js"></script>
<link href="{{< blogdown/postref >}}index_files/datatables-css/datatables-crosstalk.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/datatables-binding/datatables.js"></script>
<script src="{{< blogdown/postref >}}index_files/jquery/jquery-3.6.0.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/dt-core/css/jquery.dataTables.min.css" rel="stylesheet" />
<link href="{{< blogdown/postref >}}index_files/dt-core/css/jquery.dataTables.extra.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/dt-core/js/jquery.dataTables.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/crosstalk/css/crosstalk.min.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/crosstalk/js/crosstalk.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/jquery-sparkline/jquery.sparkline.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/jquery-sparkline/jquery.sparkline.js"></script>
<script src="{{< blogdown/postref >}}index_files/sparkline-binding/sparkline.js"></script>
<script src="{{< blogdown/postref >}}index_files/htmlwidgets/htmlwidgets.js"></script>
<link href="{{< blogdown/postref >}}index_files/datatables-css/datatables-crosstalk.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/datatables-binding/datatables.js"></script>
<script src="{{< blogdown/postref >}}index_files/jquery/jquery-3.6.0.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/dt-core/css/jquery.dataTables.min.css" rel="stylesheet" />
<link href="{{< blogdown/postref >}}index_files/dt-core/css/jquery.dataTables.extra.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/dt-core/js/jquery.dataTables.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/crosstalk/css/crosstalk.min.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/crosstalk/js/crosstalk.min.js"></script>
<script src="{{< blogdown/postref >}}index_files/htmlwidgets/htmlwidgets.js"></script>
<link href="{{< blogdown/postref >}}index_files/datatables-css/datatables-crosstalk.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/datatables-binding/datatables.js"></script>
<script src="{{< blogdown/postref >}}index_files/jquery/jquery-3.6.0.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/dt-core/css/jquery.dataTables.min.css" rel="stylesheet" />
<link href="{{< blogdown/postref >}}index_files/dt-core/css/jquery.dataTables.extra.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/dt-core/js/jquery.dataTables.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/crosstalk/css/crosstalk.min.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/crosstalk/js/crosstalk.min.js"></script>
<script src="{{< blogdown/postref >}}index_files/htmlwidgets/htmlwidgets.js"></script>
<link href="{{< blogdown/postref >}}index_files/datatables-css/datatables-crosstalk.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/datatables-binding/datatables.js"></script>
<script src="{{< blogdown/postref >}}index_files/jquery/jquery-3.6.0.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/dt-core/css/jquery.dataTables.min.css" rel="stylesheet" />
<link href="{{< blogdown/postref >}}index_files/dt-core/css/jquery.dataTables.extra.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/dt-core/js/jquery.dataTables.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/crosstalk/css/crosstalk.min.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/crosstalk/js/crosstalk.min.js"></script>
<script src="{{< blogdown/postref >}}index_files/htmlwidgets/htmlwidgets.js"></script>
<link href="{{< blogdown/postref >}}index_files/datatables-css/datatables-crosstalk.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/datatables-binding/datatables.js"></script>
<script src="{{< blogdown/postref >}}index_files/jquery/jquery-3.6.0.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/dt-core/css/jquery.dataTables.min.css" rel="stylesheet" />
<link href="{{< blogdown/postref >}}index_files/dt-core/css/jquery.dataTables.extra.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/dt-core/js/jquery.dataTables.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/crosstalk/css/crosstalk.min.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/crosstalk/js/crosstalk.min.js"></script>
<script src="{{< blogdown/postref >}}index_files/htmlwidgets/htmlwidgets.js"></script>
<link href="{{< blogdown/postref >}}index_files/datatables-css/datatables-crosstalk.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/datatables-binding/datatables.js"></script>
<script src="{{< blogdown/postref >}}index_files/jquery/jquery-3.6.0.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/dt-core/css/jquery.dataTables.min.css" rel="stylesheet" />
<link href="{{< blogdown/postref >}}index_files/dt-core/css/jquery.dataTables.extra.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/dt-core/js/jquery.dataTables.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/crosstalk/css/crosstalk.min.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/crosstalk/js/crosstalk.min.js"></script>
<script src="{{< blogdown/postref >}}index_files/htmlwidgets/htmlwidgets.js"></script>
<link href="{{< blogdown/postref >}}index_files/datatables-css/datatables-crosstalk.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/datatables-binding/datatables.js"></script>
<script src="{{< blogdown/postref >}}index_files/jquery/jquery-3.6.0.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/dt-core/css/jquery.dataTables.min.css" rel="stylesheet" />
<link href="{{< blogdown/postref >}}index_files/dt-core/css/jquery.dataTables.extra.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/dt-core/js/jquery.dataTables.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/crosstalk/css/crosstalk.min.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/crosstalk/js/crosstalk.min.js"></script>
<script src="{{< blogdown/postref >}}index_files/htmlwidgets/htmlwidgets.js"></script>
<link href="{{< blogdown/postref >}}index_files/datatables-css/datatables-crosstalk.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/datatables-binding/datatables.js"></script>
<script src="{{< blogdown/postref >}}index_files/jquery/jquery-3.6.0.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/dt-core/css/jquery.dataTables.min.css" rel="stylesheet" />
<link href="{{< blogdown/postref >}}index_files/dt-core/css/jquery.dataTables.extra.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/dt-core/js/jquery.dataTables.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/crosstalk/css/crosstalk.min.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/crosstalk/js/crosstalk.min.js"></script>
<script src="{{< blogdown/postref >}}index_files/htmlwidgets/htmlwidgets.js"></script>
<link href="{{< blogdown/postref >}}index_files/datatables-css/datatables-crosstalk.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/datatables-binding/datatables.js"></script>
<script src="{{< blogdown/postref >}}index_files/jquery/jquery-3.6.0.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/dt-core/css/jquery.dataTables.min.css" rel="stylesheet" />
<link href="{{< blogdown/postref >}}index_files/dt-core/css/jquery.dataTables.extra.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/dt-core/js/jquery.dataTables.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/crosstalk/css/crosstalk.min.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/crosstalk/js/crosstalk.min.js"></script>
<script src="{{< blogdown/postref >}}index_files/htmlwidgets/htmlwidgets.js"></script>
<link href="{{< blogdown/postref >}}index_files/datatables-css/datatables-crosstalk.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/datatables-binding/datatables.js"></script>
<script src="{{< blogdown/postref >}}index_files/jquery/jquery-3.6.0.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/dt-core/css/jquery.dataTables.min.css" rel="stylesheet" />
<link href="{{< blogdown/postref >}}index_files/dt-core/css/jquery.dataTables.extra.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/dt-core/js/jquery.dataTables.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/crosstalk/css/crosstalk.min.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/crosstalk/js/crosstalk.min.js"></script>
<script src="{{< blogdown/postref >}}index_files/htmlwidgets/htmlwidgets.js"></script>
<link href="{{< blogdown/postref >}}index_files/datatables-css/datatables-crosstalk.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/datatables-binding/datatables.js"></script>
<script src="{{< blogdown/postref >}}index_files/jquery/jquery-3.6.0.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/dt-core/css/jquery.dataTables.min.css" rel="stylesheet" />
<link href="{{< blogdown/postref >}}index_files/dt-core/css/jquery.dataTables.extra.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/dt-core/js/jquery.dataTables.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/nouislider/jquery.nouislider.min.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/nouislider/jquery.nouislider.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/selectize/selectize.bootstrap3.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/selectize/selectize.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/crosstalk/css/crosstalk.min.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/crosstalk/js/crosstalk.min.js"></script>
<script src="{{< blogdown/postref >}}index_files/htmlwidgets/htmlwidgets.js"></script>
<link href="{{< blogdown/postref >}}index_files/datatables-css/datatables-crosstalk.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/datatables-binding/datatables.js"></script>
<script src="{{< blogdown/postref >}}index_files/jquery/jquery-3.6.0.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/dt-core/css/jquery.dataTables.min.css" rel="stylesheet" />
<link href="{{< blogdown/postref >}}index_files/dt-core/css/jquery.dataTables.extra.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/dt-core/js/jquery.dataTables.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/crosstalk/css/crosstalk.min.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/crosstalk/js/crosstalk.min.js"></script>
<script src="{{< blogdown/postref >}}index_files/htmlwidgets/htmlwidgets.js"></script>
<link href="{{< blogdown/postref >}}index_files/datatables-css/datatables-crosstalk.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/datatables-binding/datatables.js"></script>
<script src="{{< blogdown/postref >}}index_files/jquery/jquery-3.6.0.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/dt-core/css/jquery.dataTables.min.css" rel="stylesheet" />
<link href="{{< blogdown/postref >}}index_files/dt-core/css/jquery.dataTables.extra.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/dt-core/js/jquery.dataTables.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/crosstalk/css/crosstalk.min.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/crosstalk/js/crosstalk.min.js"></script>
<script src="{{< blogdown/postref >}}index_files/htmlwidgets/htmlwidgets.js"></script>
<link href="{{< blogdown/postref >}}index_files/datatables-css/datatables-crosstalk.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/datatables-binding/datatables.js"></script>
<script src="{{< blogdown/postref >}}index_files/jquery/jquery-3.6.0.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/dt-core/css/jquery.dataTables.min.css" rel="stylesheet" />
<link href="{{< blogdown/postref >}}index_files/dt-core/css/jquery.dataTables.extra.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/dt-core/js/jquery.dataTables.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/crosstalk/css/crosstalk.min.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/crosstalk/js/crosstalk.min.js"></script>
<script src="{{< blogdown/postref >}}index_files/htmlwidgets/htmlwidgets.js"></script>
<link href="{{< blogdown/postref >}}index_files/datatables-css/datatables-crosstalk.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/datatables-binding/datatables.js"></script>
<script src="{{< blogdown/postref >}}index_files/jquery/jquery-3.6.0.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/dt-core/css/jquery.dataTables.min.css" rel="stylesheet" />
<link href="{{< blogdown/postref >}}index_files/dt-core/css/jquery.dataTables.extra.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/dt-core/js/jquery.dataTables.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/crosstalk/css/crosstalk.min.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/crosstalk/js/crosstalk.min.js"></script>
<script src="{{< blogdown/postref >}}index_files/htmlwidgets/htmlwidgets.js"></script>
<link href="{{< blogdown/postref >}}index_files/datatables-css/datatables-crosstalk.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/datatables-binding/datatables.js"></script>
<script src="{{< blogdown/postref >}}index_files/jquery/jquery-3.6.0.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/dt-core/css/jquery.dataTables.min.css" rel="stylesheet" />
<link href="{{< blogdown/postref >}}index_files/dt-core/css/jquery.dataTables.extra.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/dt-core/js/jquery.dataTables.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/dt-plugin-searchhighlight/source.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/dt-plugin-searchhighlight/jquery.highlight.js"></script>
<script src="{{< blogdown/postref >}}index_files/dt-plugin-searchhighlight/source.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/crosstalk/css/crosstalk.min.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/crosstalk/js/crosstalk.min.js"></script>
<script src="{{< blogdown/postref >}}index_files/htmlwidgets/htmlwidgets.js"></script>
<link href="{{< blogdown/postref >}}index_files/datatables-css/datatables-crosstalk.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/datatables-binding/datatables.js"></script>
<script src="{{< blogdown/postref >}}index_files/jquery/jquery-3.6.0.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/dt-core/css/jquery.dataTables.min.css" rel="stylesheet" />
<link href="{{< blogdown/postref >}}index_files/dt-core/css/jquery.dataTables.extra.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/dt-core/js/jquery.dataTables.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/nouislider/jquery.nouislider.min.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/nouislider/jquery.nouislider.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/selectize/selectize.bootstrap3.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/selectize/selectize.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/dt-plugin-searchhighlight/source.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/dt-plugin-searchhighlight/jquery.highlight.js"></script>
<script src="{{< blogdown/postref >}}index_files/dt-plugin-searchhighlight/source.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/crosstalk/css/crosstalk.min.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/crosstalk/js/crosstalk.min.js"></script>
<script src="{{< blogdown/postref >}}index_files/htmlwidgets/htmlwidgets.js"></script>
<link href="{{< blogdown/postref >}}index_files/datatables-css/datatables-crosstalk.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/datatables-binding/datatables.js"></script>
<script src="{{< blogdown/postref >}}index_files/jquery/jquery-3.6.0.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/dt-core/css/jquery.dataTables.min.css" rel="stylesheet" />
<link href="{{< blogdown/postref >}}index_files/dt-core/css/jquery.dataTables.extra.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/dt-core/js/jquery.dataTables.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/crosstalk/css/crosstalk.min.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/crosstalk/js/crosstalk.min.js"></script>
<script src="{{< blogdown/postref >}}index_files/htmlwidgets/htmlwidgets.js"></script>
<link href="{{< blogdown/postref >}}index_files/datatables-css/datatables-crosstalk.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/datatables-binding/datatables.js"></script>
<script src="{{< blogdown/postref >}}index_files/jquery/jquery-3.6.0.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/dt-core/css/jquery.dataTables.min.css" rel="stylesheet" />
<link href="{{< blogdown/postref >}}index_files/dt-core/css/jquery.dataTables.extra.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/dt-core/js/jquery.dataTables.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/crosstalk/css/crosstalk.min.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/crosstalk/js/crosstalk.min.js"></script>
<script src="{{< blogdown/postref >}}index_files/htmlwidgets/htmlwidgets.js"></script>
<link href="{{< blogdown/postref >}}index_files/datatables-css/datatables-crosstalk.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/datatables-binding/datatables.js"></script>
<script src="{{< blogdown/postref >}}index_files/jquery/jquery-3.6.0.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/dt-core/css/jquery.dataTables.min.css" rel="stylesheet" />
<link href="{{< blogdown/postref >}}index_files/dt-core/css/jquery.dataTables.extra.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/dt-core/js/jquery.dataTables.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/crosstalk/css/crosstalk.min.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/crosstalk/js/crosstalk.min.js"></script>
<script src="{{< blogdown/postref >}}index_files/htmlwidgets/htmlwidgets.js"></script>
<link href="{{< blogdown/postref >}}index_files/datatables-css/datatables-crosstalk.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/datatables-binding/datatables.js"></script>
<script src="{{< blogdown/postref >}}index_files/jquery/jquery-3.6.0.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/dt-core/css/jquery.dataTables.min.css" rel="stylesheet" />
<link href="{{< blogdown/postref >}}index_files/dt-core/css/jquery.dataTables.extra.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/dt-core/js/jquery.dataTables.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/crosstalk/css/crosstalk.min.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/crosstalk/js/crosstalk.min.js"></script>
<script src="{{< blogdown/postref >}}index_files/htmlwidgets/htmlwidgets.js"></script>
<link href="{{< blogdown/postref >}}index_files/datatables-css/datatables-crosstalk.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/datatables-binding/datatables.js"></script>
<script src="{{< blogdown/postref >}}index_files/jquery/jquery-3.6.0.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/dt-core/css/jquery.dataTables.min.css" rel="stylesheet" />
<link href="{{< blogdown/postref >}}index_files/dt-core/css/jquery.dataTables.extra.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/dt-core/js/jquery.dataTables.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/crosstalk/css/crosstalk.min.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/crosstalk/js/crosstalk.min.js"></script>
<script src="{{< blogdown/postref >}}index_files/htmlwidgets/htmlwidgets.js"></script>
<link href="{{< blogdown/postref >}}index_files/datatables-css/datatables-crosstalk.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/datatables-binding/datatables.js"></script>
<script src="{{< blogdown/postref >}}index_files/jquery/jquery-3.6.0.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/dt-core/css/jquery.dataTables.min.css" rel="stylesheet" />
<link href="{{< blogdown/postref >}}index_files/dt-core/css/jquery.dataTables.extra.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/dt-core/js/jquery.dataTables.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/dt-ext-fixedcolumns/css/fixedColumns.dataTables.min.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/dt-ext-fixedcolumns/js/dataTables.fixedColumns.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/crosstalk/css/crosstalk.min.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/crosstalk/js/crosstalk.min.js"></script>
<script src="{{< blogdown/postref >}}index_files/htmlwidgets/htmlwidgets.js"></script>
<link href="{{< blogdown/postref >}}index_files/datatables-css/datatables-crosstalk.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/datatables-binding/datatables.js"></script>
<script src="{{< blogdown/postref >}}index_files/jquery/jquery-3.6.0.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/dt-core/css/jquery.dataTables.min.css" rel="stylesheet" />
<link href="{{< blogdown/postref >}}index_files/dt-core/css/jquery.dataTables.extra.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/dt-core/js/jquery.dataTables.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/dt-ext-colreorder/css/colReorder.dataTables.min.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/dt-ext-colreorder/js/dataTables.colReorder.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/crosstalk/css/crosstalk.min.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/crosstalk/js/crosstalk.min.js"></script>
<script src="{{< blogdown/postref >}}index_files/htmlwidgets/htmlwidgets.js"></script>
<link href="{{< blogdown/postref >}}index_files/datatables-css/datatables-crosstalk.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/datatables-binding/datatables.js"></script>
<script src="{{< blogdown/postref >}}index_files/jquery/jquery-3.6.0.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/dt-core/css/jquery.dataTables.min.css" rel="stylesheet" />
<link href="{{< blogdown/postref >}}index_files/dt-core/css/jquery.dataTables.extra.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/dt-core/js/jquery.dataTables.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/dt-ext-colreorder/css/colReorder.dataTables.min.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/dt-ext-colreorder/js/dataTables.colReorder.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/crosstalk/css/crosstalk.min.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/crosstalk/js/crosstalk.min.js"></script>
<script src="{{< blogdown/postref >}}index_files/htmlwidgets/htmlwidgets.js"></script>
<link href="{{< blogdown/postref >}}index_files/datatables-css/datatables-crosstalk.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/datatables-binding/datatables.js"></script>
<script src="{{< blogdown/postref >}}index_files/jquery/jquery-3.6.0.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/dt-core/css/jquery.dataTables.min.css" rel="stylesheet" />
<link href="{{< blogdown/postref >}}index_files/dt-core/css/jquery.dataTables.extra.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/dt-core/js/jquery.dataTables.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/dt-ext-colreorder/css/colReorder.dataTables.min.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/dt-ext-colreorder/js/dataTables.colReorder.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/crosstalk/css/crosstalk.min.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/crosstalk/js/crosstalk.min.js"></script>
<script src="{{< blogdown/postref >}}index_files/htmlwidgets/htmlwidgets.js"></script>
<link href="{{< blogdown/postref >}}index_files/datatables-css/datatables-crosstalk.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/datatables-binding/datatables.js"></script>
<script src="{{< blogdown/postref >}}index_files/jquery/jquery-3.6.0.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/dt-core/css/jquery.dataTables.min.css" rel="stylesheet" />
<link href="{{< blogdown/postref >}}index_files/dt-core/css/jquery.dataTables.extra.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/dt-core/js/jquery.dataTables.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/dt-ext-rowreorder/css/rowReorder.dataTables.min.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/dt-ext-rowreorder/js/dataTables.rowReorder.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/crosstalk/css/crosstalk.min.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/crosstalk/js/crosstalk.min.js"></script>
<script src="{{< blogdown/postref >}}index_files/htmlwidgets/htmlwidgets.js"></script>
<link href="{{< blogdown/postref >}}index_files/datatables-css/datatables-crosstalk.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/datatables-binding/datatables.js"></script>
<script src="{{< blogdown/postref >}}index_files/jquery/jquery-3.6.0.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/dt-core/css/jquery.dataTables.min.css" rel="stylesheet" />
<link href="{{< blogdown/postref >}}index_files/dt-core/css/jquery.dataTables.extra.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/dt-core/js/jquery.dataTables.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/dt-ext-rowreorder/css/rowReorder.dataTables.min.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/dt-ext-rowreorder/js/dataTables.rowReorder.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/crosstalk/css/crosstalk.min.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/crosstalk/js/crosstalk.min.js"></script>
<script src="{{< blogdown/postref >}}index_files/htmlwidgets/htmlwidgets.js"></script>
<link href="{{< blogdown/postref >}}index_files/datatables-css/datatables-crosstalk.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/datatables-binding/datatables.js"></script>
<script src="{{< blogdown/postref >}}index_files/jquery/jquery-3.6.0.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/dt-core/css/jquery.dataTables.min.css" rel="stylesheet" />
<link href="{{< blogdown/postref >}}index_files/dt-core/css/jquery.dataTables.extra.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/dt-core/js/jquery.dataTables.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/dt-ext-rowgroup/css/rowGroup.dataTables.min.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/dt-ext-rowgroup/js/dataTables.rowGroup.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/crosstalk/css/crosstalk.min.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/crosstalk/js/crosstalk.min.js"></script>
<script src="{{< blogdown/postref >}}index_files/htmlwidgets/htmlwidgets.js"></script>
<link href="{{< blogdown/postref >}}index_files/datatables-css/datatables-crosstalk.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/datatables-binding/datatables.js"></script>
<script src="{{< blogdown/postref >}}index_files/jquery/jquery-3.6.0.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/dt-core/css/jquery.dataTables.min.css" rel="stylesheet" />
<link href="{{< blogdown/postref >}}index_files/dt-core/css/jquery.dataTables.extra.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/dt-core/js/jquery.dataTables.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/dt-ext-rowgroup/css/rowGroup.dataTables.min.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/dt-ext-rowgroup/js/dataTables.rowGroup.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/crosstalk/css/crosstalk.min.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/crosstalk/js/crosstalk.min.js"></script>
<script src="{{< blogdown/postref >}}index_files/htmlwidgets/htmlwidgets.js"></script>
<link href="{{< blogdown/postref >}}index_files/datatables-css/datatables-crosstalk.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/datatables-binding/datatables.js"></script>
<script src="{{< blogdown/postref >}}index_files/jquery/jquery-3.6.0.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/dt-core/css/jquery.dataTables.min.css" rel="stylesheet" />
<link href="{{< blogdown/postref >}}index_files/dt-core/css/jquery.dataTables.extra.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/dt-core/js/jquery.dataTables.min.js"></script>
<script src="{{< blogdown/postref >}}index_files/jszip/jszip.min.js"></script>
<script src="{{< blogdown/postref >}}index_files/pdfmake/pdfmake.js"></script>
<script src="{{< blogdown/postref >}}index_files/pdfmake/vfs_fonts.js"></script>
<link href="{{< blogdown/postref >}}index_files/dt-ext-buttons/css/buttons.dataTables.min.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/dt-ext-buttons/js/dataTables.buttons.min.js"></script>
<script src="{{< blogdown/postref >}}index_files/dt-ext-buttons/js/buttons.html5.min.js"></script>
<script src="{{< blogdown/postref >}}index_files/dt-ext-buttons/js/buttons.colVis.min.js"></script>
<script src="{{< blogdown/postref >}}index_files/dt-ext-buttons/js/buttons.print.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/crosstalk/css/crosstalk.min.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/crosstalk/js/crosstalk.min.js"></script>
<script src="{{< blogdown/postref >}}index_files/htmlwidgets/htmlwidgets.js"></script>
<link href="{{< blogdown/postref >}}index_files/datatables-css/datatables-crosstalk.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/datatables-binding/datatables.js"></script>
<script src="{{< blogdown/postref >}}index_files/jquery/jquery-3.6.0.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/dt-core/css/jquery.dataTables.min.css" rel="stylesheet" />
<link href="{{< blogdown/postref >}}index_files/dt-core/css/jquery.dataTables.extra.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/dt-core/js/jquery.dataTables.min.js"></script>
<script src="{{< blogdown/postref >}}index_files/jszip/jszip.min.js"></script>
<script src="{{< blogdown/postref >}}index_files/pdfmake/pdfmake.js"></script>
<script src="{{< blogdown/postref >}}index_files/pdfmake/vfs_fonts.js"></script>
<link href="{{< blogdown/postref >}}index_files/dt-ext-buttons/css/buttons.dataTables.min.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/dt-ext-buttons/js/dataTables.buttons.min.js"></script>
<script src="{{< blogdown/postref >}}index_files/dt-ext-buttons/js/buttons.html5.min.js"></script>
<script src="{{< blogdown/postref >}}index_files/dt-ext-buttons/js/buttons.colVis.min.js"></script>
<script src="{{< blogdown/postref >}}index_files/dt-ext-buttons/js/buttons.print.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/crosstalk/css/crosstalk.min.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/crosstalk/js/crosstalk.min.js"></script>
<script src="{{< blogdown/postref >}}index_files/htmlwidgets/htmlwidgets.js"></script>
<link href="{{< blogdown/postref >}}index_files/datatables-css/datatables-crosstalk.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/datatables-binding/datatables.js"></script>
<script src="{{< blogdown/postref >}}index_files/jquery/jquery-3.6.0.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/dt-core/css/jquery.dataTables.min.css" rel="stylesheet" />
<link href="{{< blogdown/postref >}}index_files/dt-core/css/jquery.dataTables.extra.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/dt-core/js/jquery.dataTables.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/dt-ext-buttons/css/buttons.dataTables.min.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/dt-ext-buttons/js/dataTables.buttons.min.js"></script>
<script src="{{< blogdown/postref >}}index_files/dt-ext-buttons/js/buttons.html5.min.js"></script>
<script src="{{< blogdown/postref >}}index_files/dt-ext-buttons/js/buttons.colVis.min.js"></script>
<script src="{{< blogdown/postref >}}index_files/dt-ext-buttons/js/buttons.print.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/crosstalk/css/crosstalk.min.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/crosstalk/js/crosstalk.min.js"></script>
<script src="{{< blogdown/postref >}}index_files/htmlwidgets/htmlwidgets.js"></script>
<link href="{{< blogdown/postref >}}index_files/datatables-css/datatables-crosstalk.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/datatables-binding/datatables.js"></script>
<script src="{{< blogdown/postref >}}index_files/jquery/jquery-3.6.0.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/dt-core/css/jquery.dataTables.min.css" rel="stylesheet" />
<link href="{{< blogdown/postref >}}index_files/dt-core/css/jquery.dataTables.extra.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/dt-core/js/jquery.dataTables.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/dt-ext-buttons/css/buttons.dataTables.min.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/dt-ext-buttons/js/dataTables.buttons.min.js"></script>
<script src="{{< blogdown/postref >}}index_files/dt-ext-buttons/js/buttons.html5.min.js"></script>
<script src="{{< blogdown/postref >}}index_files/dt-ext-buttons/js/buttons.colVis.min.js"></script>
<script src="{{< blogdown/postref >}}index_files/dt-ext-buttons/js/buttons.print.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/crosstalk/css/crosstalk.min.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/crosstalk/js/crosstalk.min.js"></script>
<script src="{{< blogdown/postref >}}index_files/htmlwidgets/htmlwidgets.js"></script>
<link href="{{< blogdown/postref >}}index_files/datatables-css/datatables-crosstalk.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/datatables-binding/datatables.js"></script>
<script src="{{< blogdown/postref >}}index_files/jquery/jquery-3.6.0.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/dt-core/css/jquery.dataTables.min.css" rel="stylesheet" />
<link href="{{< blogdown/postref >}}index_files/dt-core/css/jquery.dataTables.extra.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/dt-core/js/jquery.dataTables.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/dt-ext-buttons/css/buttons.dataTables.min.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/dt-ext-buttons/js/dataTables.buttons.min.js"></script>
<script src="{{< blogdown/postref >}}index_files/dt-ext-buttons/js/buttons.html5.min.js"></script>
<script src="{{< blogdown/postref >}}index_files/dt-ext-buttons/js/buttons.colVis.min.js"></script>
<script src="{{< blogdown/postref >}}index_files/dt-ext-buttons/js/buttons.print.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/crosstalk/css/crosstalk.min.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/crosstalk/js/crosstalk.min.js"></script>
<script src="{{< blogdown/postref >}}index_files/htmlwidgets/htmlwidgets.js"></script>
<link href="{{< blogdown/postref >}}index_files/datatables-css/datatables-crosstalk.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/datatables-binding/datatables.js"></script>
<script src="{{< blogdown/postref >}}index_files/jquery/jquery-3.6.0.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/dt-core/css/jquery.dataTables.min.css" rel="stylesheet" />
<link href="{{< blogdown/postref >}}index_files/dt-core/css/jquery.dataTables.extra.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/dt-core/js/jquery.dataTables.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/dt-ext-buttons/css/buttons.dataTables.min.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/dt-ext-buttons/js/dataTables.buttons.min.js"></script>
<script src="{{< blogdown/postref >}}index_files/dt-ext-buttons/js/buttons.html5.min.js"></script>
<script src="{{< blogdown/postref >}}index_files/dt-ext-buttons/js/buttons.colVis.min.js"></script>
<script src="{{< blogdown/postref >}}index_files/dt-ext-buttons/js/buttons.print.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/crosstalk/css/crosstalk.min.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/crosstalk/js/crosstalk.min.js"></script>
<script src="{{< blogdown/postref >}}index_files/htmlwidgets/htmlwidgets.js"></script>
<link href="{{< blogdown/postref >}}index_files/datatables-css/datatables-crosstalk.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/datatables-binding/datatables.js"></script>
<script src="{{< blogdown/postref >}}index_files/jquery/jquery-3.6.0.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/dt-core/css/jquery.dataTables.min.css" rel="stylesheet" />
<link href="{{< blogdown/postref >}}index_files/dt-core/css/jquery.dataTables.extra.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/dt-core/js/jquery.dataTables.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/dt-ext-buttons/css/buttons.dataTables.min.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/dt-ext-buttons/js/dataTables.buttons.min.js"></script>
<script src="{{< blogdown/postref >}}index_files/dt-ext-buttons/js/buttons.html5.min.js"></script>
<script src="{{< blogdown/postref >}}index_files/dt-ext-buttons/js/buttons.colVis.min.js"></script>
<script src="{{< blogdown/postref >}}index_files/dt-ext-buttons/js/buttons.print.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/crosstalk/css/crosstalk.min.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/crosstalk/js/crosstalk.min.js"></script>
<script src="{{< blogdown/postref >}}index_files/htmlwidgets/htmlwidgets.js"></script>
<link href="{{< blogdown/postref >}}index_files/datatables-css/datatables-crosstalk.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/datatables-binding/datatables.js"></script>
<script src="{{< blogdown/postref >}}index_files/jquery/jquery-3.6.0.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/dt-core/css/jquery.dataTables.min.css" rel="stylesheet" />
<link href="{{< blogdown/postref >}}index_files/dt-core/css/jquery.dataTables.extra.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/dt-core/js/jquery.dataTables.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/crosstalk/css/crosstalk.min.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/crosstalk/js/crosstalk.min.js"></script>
<script src="{{< blogdown/postref >}}index_files/htmlwidgets/htmlwidgets.js"></script>
<script src="{{< blogdown/postref >}}index_files/plotly-binding/plotly.js"></script>
<script src="{{< blogdown/postref >}}index_files/typedarray/typedarray.min.js"></script>
<script src="{{< blogdown/postref >}}index_files/jquery/jquery-3.6.0.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/crosstalk/css/crosstalk.min.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/crosstalk/js/crosstalk.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/plotly-htmlwidgets-css/plotly-htmlwidgets.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/plotly-main/plotly-latest.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/datatables-css/datatables-crosstalk.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/datatables-binding/datatables.js"></script>
<link href="{{< blogdown/postref >}}index_files/dt-core/css/jquery.dataTables.min.css" rel="stylesheet" />
<link href="{{< blogdown/postref >}}index_files/dt-core/css/jquery.dataTables.extra.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/dt-core/js/jquery.dataTables.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/nouislider/jquery.nouislider.min.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/nouislider/jquery.nouislider.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/selectize/selectize.bootstrap3.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/selectize/selectize.min.js"></script>
<meta name="viewport" content="width=device-width, initial-scale=1" />

<link href="{{< blogdown/postref >}}index_files/bootstrap-grid/bootstrap-grid.min.css" rel="stylesheet" />

这是一份针对 R 中的表格包子[^1] DT 的速查手册。DT 包源自于 JavaScripts（以下简称 JS） 中的 DataTables，但并非所有 DataTables 提供的功能都能在 DT 中实现，而 DT 中也有独立于 DataTables 之外的一些更贴合 R 语法的函数。

> 本文使用的 DT 包版本为0.26。

全文共两个章节：

-   1.静态样式：表格基础（高度、宽度、行名、列名），表格元素（多行表头、标题、脚注），表格样式（表头或表格主体的外框线、字体、背景填充等），数据格式（插入 Unicode 字符、超链接、图片、字体图标、迷你图），样式冲突问题。

-   2.动态效果：表格控件，语言文字，筛选，排序，扩展动能等。

# 第一章 静态样式

在正式绘制表格之前，先编造一份数据便于后续复现。

``` r
library(DT)
library(data.table)

set.seed(2022)
data <- data.frame(
  type1 = sort(rep(LETTERS[1:20], 2)), 
  type2 = rep(c('NO', 'YES'), 20),
  value = sample(2000:5000, 40),
  value1 = sample(200:2000, 40),
  value2 = sample(200:2000, 40),
  prob1 = sample(1:100, 40) / 100,
  prob2 = sample(-50:50, 40) / 100
)

#设置全局选项，本文档中所有表格每页仅显示5行
options(DT.options = list(pageLength = 5, dom = 'ftip'))
```

## 1.0.基本说明

DT 包并不是一个完全独立且封闭的 R 表格系统，作为一个以动态交互功能为主的表格包，在设置静态样式方面往往需要引入 html、css。因此本小节对后文中需要明晰的一些术语概念，及引入其他语言的一些基本方法做一些说明。

### 1.0.1.术语约定

为了不使描述几种语言的特性时，因为各种术语互相混淆导致影响阅读，笔者特别对以下术语的含义做出如下约定。

元素：源于 html 元素，表格元素是构成表格的基本组成部分，如表格的表头、表格主体、标题、脚注、行、列、单元格等。

样式：源于 css 样式，设置样式可对各表格元素进行修饰，如表格的边框样式、表格所展示数据的字体样式等。

属性：元素有具体的元素属性，样式有具体的样式属性。

参数/参数值：R 函数中能够输入可选内容的变量称为参数，每个参数能够输入的具体值称为参数值。比如对表格某一列设置宽度为’300px’时，对应的参数和参数值就是 `width = '300px'`。

### 1.0.2.参数位置

DT 中可设置的参数非常多，可以同时为多个表设置共用的全局参数，也可以为单个表单独设置参数，或进一步为单个表中的一列或多列单独设置参数。

``` r
# 多个表时设置全局参数
options(DT.options = list(...))

# 为单个表设置参数
datatable(
  data,
  extensions = NULL, # 扩展功能
  plugins = NULL, # 插件
  ...,
  options = list(...,
                 # 为目标列设置参数
                 columnDefs = list( 
                   list(targets = NULL, ...),
                   list(targets = NULL, ...)
                 )))
```

### 1.0.3.回调函数

回调函数的作用是在 R 中引入 JS，引入 JS 就可以引入 html 和 css，从而丰富表格元素以及为表格设定样式。DataTables 中的 回调函数有好几种，所起到的作用也各不相同。

第一种，回调函数 `callback = JS("")`，基本写法如下。

``` r
datatable(data,
          callback = JS(""))
```

第二种，初始化回调函数 `initComplete = JS("")`，基本写法如下。

``` r
datatable(data,
          options = list(initComplete = JS("function(settings, json) {}")))
```

第三种，针对行的回调函数 `rowCallback = JS("")`，基本写法如下。

``` r
datatable(data,
          options = list(rowCallback = JS("function(row, data) {}")))
```

第四种，针对列的渲染 `render = JS("")`，基本写法如下。

``` r
datatable(data, options = list(
  columnDefs = list(
    list(targets = NULL, render = JS("function(data, type, row, meta) {}"))
)))
```

还有针对表头的回调函数 headerCallback，针对每次分页绘图渲染的回调函数 drawCallback 等等。值得一提的是，既然都可以写入 JS，那么事实上调用不同的回调函数有时也可以达到相同的效果。比如在后文1.5.1小节中，可以通过调用初始化回调函数来修改表头的 css 样式，其实也可以直接调用针对表头的回调函数来实现。

``` r
datatable(data,
          options = list(
            headerCallback = JS(
              "function(thead, data, start, end, display){
   $('th', thead).css('color', 'green');}")))
```

## 1.1.表格基础

### 1.1.0.高度（height）、宽度（width）

一般情况下，表格的高度和宽度是与显示页面的大小自适应的，也可以单独设置整个表格的高度和宽度。

-   设置整个表格的高度和宽度。

``` r
datatable(data, height = 250, width = 600)
```

-   单独设置某一列或多列的宽度。

``` r
datatable(data,
          options = list(autoWidth = TRUE,
                         columnDefs = list(list(
                           width = '300px', targets = c(1, 2)
                         ))))
```

<div id="htmlwidget-1" style="width:100%;height:auto;" class="datatables html-widget"></div>
<script type="application/json" data-for="htmlwidget-1">{"x":{"filter":"none","vertical":false,"data":[["1","2","3","4","5","6","7","8","9","10","11","12","13","14","15","16","17","18","19","20","21","22","23","24","25","26","27","28","29","30","31","32","33","34","35","36","37","38","39","40"],["A","A","B","B","C","C","D","D","E","E","F","F","G","G","H","H","I","I","J","J","K","K","L","L","M","M","N","N","O","O","P","P","Q","Q","R","R","S","S","T","T"],["NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES"],[2227,3458,4870,2707,2773,4750,2475,2122,4280,3293,3271,3521,2950,4159,4517,3988,2512,2799,4496,4425,4716,3547,3998,2827,2427,3989,2358,4197,2987,3130,2275,3597,3607,4499,2796,2193,4631,2492,4303,2233],[1134,1576,1510,1279,1224,581,1242,700,1529,624,1584,1471,202,1211,1726,1255,1855,616,1834,1953,987,1441,798,1542,550,1715,1100,1047,1777,1929,543,735,1688,1683,345,1601,1420,1333,1229,958],[1502,1327,1647,1188,1430,1768,806,1875,565,1024,528,1258,603,490,935,438,301,1751,1161,1276,1606,1665,376,783,1143,1560,1571,663,697,1596,726,1128,313,1410,1020,1444,1935,1816,1346,912],[0.39,0.02,0.19,0.29,0.54,0.03,0.04,0.36,0.47,0.38,0.69,0.65,0.46,0.2,0.26,0.77,0.86,0.59,0.22,0.34,0.63,0.83,0.89,0.42,0.94,0.45,0.95,0.58,0.01,0.28,0.32,0.96,0.07,0.76,0.13,0.05,0.85,0.75,0.31,0.23],[-0.02,0.01,0.28,0.12,0.32,0,-0.5,-0.01,0.27,0.24,-0.11,-0.4,-0.06,0.31,0.15,0.41,0.42,-0.05,-0.16,-0.48,0.18,-0.45,0.05,0.02,0.43,0.04,-0.46,-0.25,-0.14,0.37,0.16,-0.34,-0.32,0.44,0.26,-0.43,-0.13,-0.42,-0.09,-0.2]],"container":"<table class=\"display\">\n  <thead>\n    <tr>\n      <th> <\/th>\n      <th>type1<\/th>\n      <th>type2<\/th>\n      <th>value<\/th>\n      <th>value1<\/th>\n      <th>value2<\/th>\n      <th>prob1<\/th>\n      <th>prob2<\/th>\n    <\/tr>\n  <\/thead>\n<\/table>","options":{"pageLength":5,"dom":"ftip","autoWidth":true,"columnDefs":[{"width":"300px","targets":[1,2]},{"className":"dt-right","targets":[3,4,5,6,7]},{"orderable":false,"targets":0}],"order":[],"orderClasses":false,"lengthMenu":[5,10,25,50,100]}},"evals":[],"jsHooks":[]}</script>

### 1.1.1.行名（rownames）

对应修改行名称的参数是 rownames，可填入的具体参数值可以是 TRUE/FALSE，或者字符向量。

DT 包中列的序号由0开始，当行名称显示出来时，行名称那一列就是序号第0列，表格中第1列数据是序号第1列；当行名称隐藏时，表格中的第1列数据是序号上的第0列。

-   当 `rownames = TRUE` 时，若原数据自带行名称，则显示其行名称；若原数据不带有行名称，则显示以1开始的连续数字序号。
-   当 `rownames = FALSE` 时，隐藏行名称。
-   自定义行名称时，需要填入一个字符向量，这个向量的长度应该跟表格的行数保持一致。

``` r
datatable(data, rownames = c(paste('第', 1:nrow(data), '行')))
```

<div id="htmlwidget-2" style="width:100%;height:auto;" class="datatables html-widget"></div>
<script type="application/json" data-for="htmlwidget-2">{"x":{"filter":"none","vertical":false,"data":[["第 1 行","第 2 行","第 3 行","第 4 行","第 5 行","第 6 行","第 7 行","第 8 行","第 9 行","第 10 行","第 11 行","第 12 行","第 13 行","第 14 行","第 15 行","第 16 行","第 17 行","第 18 行","第 19 行","第 20 行","第 21 行","第 22 行","第 23 行","第 24 行","第 25 行","第 26 行","第 27 行","第 28 行","第 29 行","第 30 行","第 31 行","第 32 行","第 33 行","第 34 行","第 35 行","第 36 行","第 37 行","第 38 行","第 39 行","第 40 行"],["A","A","B","B","C","C","D","D","E","E","F","F","G","G","H","H","I","I","J","J","K","K","L","L","M","M","N","N","O","O","P","P","Q","Q","R","R","S","S","T","T"],["NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES"],[2227,3458,4870,2707,2773,4750,2475,2122,4280,3293,3271,3521,2950,4159,4517,3988,2512,2799,4496,4425,4716,3547,3998,2827,2427,3989,2358,4197,2987,3130,2275,3597,3607,4499,2796,2193,4631,2492,4303,2233],[1134,1576,1510,1279,1224,581,1242,700,1529,624,1584,1471,202,1211,1726,1255,1855,616,1834,1953,987,1441,798,1542,550,1715,1100,1047,1777,1929,543,735,1688,1683,345,1601,1420,1333,1229,958],[1502,1327,1647,1188,1430,1768,806,1875,565,1024,528,1258,603,490,935,438,301,1751,1161,1276,1606,1665,376,783,1143,1560,1571,663,697,1596,726,1128,313,1410,1020,1444,1935,1816,1346,912],[0.39,0.02,0.19,0.29,0.54,0.03,0.04,0.36,0.47,0.38,0.69,0.65,0.46,0.2,0.26,0.77,0.86,0.59,0.22,0.34,0.63,0.83,0.89,0.42,0.94,0.45,0.95,0.58,0.01,0.28,0.32,0.96,0.07,0.76,0.13,0.05,0.85,0.75,0.31,0.23],[-0.02,0.01,0.28,0.12,0.32,0,-0.5,-0.01,0.27,0.24,-0.11,-0.4,-0.06,0.31,0.15,0.41,0.42,-0.05,-0.16,-0.48,0.18,-0.45,0.05,0.02,0.43,0.04,-0.46,-0.25,-0.14,0.37,0.16,-0.34,-0.32,0.44,0.26,-0.43,-0.13,-0.42,-0.09,-0.2]],"container":"<table class=\"display\">\n  <thead>\n    <tr>\n      <th> <\/th>\n      <th>type1<\/th>\n      <th>type2<\/th>\n      <th>value<\/th>\n      <th>value1<\/th>\n      <th>value2<\/th>\n      <th>prob1<\/th>\n      <th>prob2<\/th>\n    <\/tr>\n  <\/thead>\n<\/table>","options":{"pageLength":5,"dom":"ftip","columnDefs":[{"className":"dt-right","targets":[3,4,5,6,7]},{"orderable":false,"targets":0}],"order":[],"autoWidth":false,"orderClasses":false,"lengthMenu":[5,10,25,50,100]}},"evals":[],"jsHooks":[]}</script>

### 1.1.2.列名（colnames）

对应修改列名称的参数是 rownames，可以指定部分列进行修改，也可以一次修改全部列的列名称。

-   若需将列名称全部替换，须设置一个与表格列数等长的字符向量。

``` r
# 为第0列（序号列）也修改列名称
# datatable(data, colnames = c(paste('第', 0:ncol(data), '列')))

datatable(data, colnames = c(paste('第', 1:ncol(data), '列')))
```

<div id="htmlwidget-3" style="width:100%;height:auto;" class="datatables html-widget"></div>
<script type="application/json" data-for="htmlwidget-3">{"x":{"filter":"none","vertical":false,"data":[["1","2","3","4","5","6","7","8","9","10","11","12","13","14","15","16","17","18","19","20","21","22","23","24","25","26","27","28","29","30","31","32","33","34","35","36","37","38","39","40"],["A","A","B","B","C","C","D","D","E","E","F","F","G","G","H","H","I","I","J","J","K","K","L","L","M","M","N","N","O","O","P","P","Q","Q","R","R","S","S","T","T"],["NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES"],[2227,3458,4870,2707,2773,4750,2475,2122,4280,3293,3271,3521,2950,4159,4517,3988,2512,2799,4496,4425,4716,3547,3998,2827,2427,3989,2358,4197,2987,3130,2275,3597,3607,4499,2796,2193,4631,2492,4303,2233],[1134,1576,1510,1279,1224,581,1242,700,1529,624,1584,1471,202,1211,1726,1255,1855,616,1834,1953,987,1441,798,1542,550,1715,1100,1047,1777,1929,543,735,1688,1683,345,1601,1420,1333,1229,958],[1502,1327,1647,1188,1430,1768,806,1875,565,1024,528,1258,603,490,935,438,301,1751,1161,1276,1606,1665,376,783,1143,1560,1571,663,697,1596,726,1128,313,1410,1020,1444,1935,1816,1346,912],[0.39,0.02,0.19,0.29,0.54,0.03,0.04,0.36,0.47,0.38,0.69,0.65,0.46,0.2,0.26,0.77,0.86,0.59,0.22,0.34,0.63,0.83,0.89,0.42,0.94,0.45,0.95,0.58,0.01,0.28,0.32,0.96,0.07,0.76,0.13,0.05,0.85,0.75,0.31,0.23],[-0.02,0.01,0.28,0.12,0.32,0,-0.5,-0.01,0.27,0.24,-0.11,-0.4,-0.06,0.31,0.15,0.41,0.42,-0.05,-0.16,-0.48,0.18,-0.45,0.05,0.02,0.43,0.04,-0.46,-0.25,-0.14,0.37,0.16,-0.34,-0.32,0.44,0.26,-0.43,-0.13,-0.42,-0.09,-0.2]],"container":"<table class=\"display\">\n  <thead>\n    <tr>\n      <th> <\/th>\n      <th>第 1 列<\/th>\n      <th>第 2 列<\/th>\n      <th>第 3 列<\/th>\n      <th>第 4 列<\/th>\n      <th>第 5 列<\/th>\n      <th>第 6 列<\/th>\n      <th>第 7 列<\/th>\n    <\/tr>\n  <\/thead>\n<\/table>","options":{"pageLength":5,"dom":"ftip","columnDefs":[{"className":"dt-right","targets":[3,4,5,6,7]},{"orderable":false,"targets":0}],"order":[],"autoWidth":false,"orderClasses":false,"lengthMenu":[5,10,25,50,100]}},"evals":[],"jsHooks":[]}</script>

-   若仅替换部分列名称，可如此指定需要替换列名称的列，以及新的名称。当用列的序号指代列时，最好隐藏行名称，免得弄混。

``` r
# 方式一，用列的序号指代列
# datatable(data, rownames = FALSE, colnames = c('第1列' = 1, '第2列' = 2))

# 方式二，用列的名称指代列
datatable(data, colnames = c('第1列' = 'type1', '第2列' = 'type2'))
```

<div id="htmlwidget-4" style="width:100%;height:auto;" class="datatables html-widget"></div>
<script type="application/json" data-for="htmlwidget-4">{"x":{"filter":"none","vertical":false,"data":[["1","2","3","4","5","6","7","8","9","10","11","12","13","14","15","16","17","18","19","20","21","22","23","24","25","26","27","28","29","30","31","32","33","34","35","36","37","38","39","40"],["A","A","B","B","C","C","D","D","E","E","F","F","G","G","H","H","I","I","J","J","K","K","L","L","M","M","N","N","O","O","P","P","Q","Q","R","R","S","S","T","T"],["NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES"],[2227,3458,4870,2707,2773,4750,2475,2122,4280,3293,3271,3521,2950,4159,4517,3988,2512,2799,4496,4425,4716,3547,3998,2827,2427,3989,2358,4197,2987,3130,2275,3597,3607,4499,2796,2193,4631,2492,4303,2233],[1134,1576,1510,1279,1224,581,1242,700,1529,624,1584,1471,202,1211,1726,1255,1855,616,1834,1953,987,1441,798,1542,550,1715,1100,1047,1777,1929,543,735,1688,1683,345,1601,1420,1333,1229,958],[1502,1327,1647,1188,1430,1768,806,1875,565,1024,528,1258,603,490,935,438,301,1751,1161,1276,1606,1665,376,783,1143,1560,1571,663,697,1596,726,1128,313,1410,1020,1444,1935,1816,1346,912],[0.39,0.02,0.19,0.29,0.54,0.03,0.04,0.36,0.47,0.38,0.69,0.65,0.46,0.2,0.26,0.77,0.86,0.59,0.22,0.34,0.63,0.83,0.89,0.42,0.94,0.45,0.95,0.58,0.01,0.28,0.32,0.96,0.07,0.76,0.13,0.05,0.85,0.75,0.31,0.23],[-0.02,0.01,0.28,0.12,0.32,0,-0.5,-0.01,0.27,0.24,-0.11,-0.4,-0.06,0.31,0.15,0.41,0.42,-0.05,-0.16,-0.48,0.18,-0.45,0.05,0.02,0.43,0.04,-0.46,-0.25,-0.14,0.37,0.16,-0.34,-0.32,0.44,0.26,-0.43,-0.13,-0.42,-0.09,-0.2]],"container":"<table class=\"display\">\n  <thead>\n    <tr>\n      <th> <\/th>\n      <th>第1列<\/th>\n      <th>第2列<\/th>\n      <th>value<\/th>\n      <th>value1<\/th>\n      <th>value2<\/th>\n      <th>prob1<\/th>\n      <th>prob2<\/th>\n    <\/tr>\n  <\/thead>\n<\/table>","options":{"pageLength":5,"dom":"ftip","columnDefs":[{"className":"dt-right","targets":[3,4,5,6,7]},{"orderable":false,"targets":0}],"order":[],"autoWidth":false,"orderClasses":false,"lengthMenu":[5,10,25,50,100]}},"evals":[],"jsHooks":[]}</script>

## 1.2.引入 htmltools 丰富表格元素

在 DT 包中若要给表格添加更多元素，如多行表头、表格标题、表格脚注等，需要引入 htmltools 包，这相当于在 R 中引入 html。DT 包中引入 htmltools 的方式有两种：其一，从 DT 包已有参数中引入，比如 caption 和 container；其二，把整个表格引入一个纯 html 的 div 框中。

在引入 htmltools 的同时也可引入 css 来修改样式。

### 1.2.1.从标题（caption）中引入

#### 1.2.1.1.表格标题

表格标题，也可称为题注，位置通常在表格的上方。DT 包中对应修改表格标题的参数是 caption，具体参数值可填入一个字符串，或者引入 htmltools。

若只是填入字符串，那么表格标题的样式无法单独设置，只能使用默认样式。

``` r
datatable(data, caption = '表1：一个表格的标题')
```

<div id="htmlwidget-5" style="width:100%;height:auto;" class="datatables html-widget"></div>
<script type="application/json" data-for="htmlwidget-5">{"x":{"filter":"none","vertical":false,"caption":"<caption>表1：一个表格的标题<\/caption>","data":[["1","2","3","4","5","6","7","8","9","10","11","12","13","14","15","16","17","18","19","20","21","22","23","24","25","26","27","28","29","30","31","32","33","34","35","36","37","38","39","40"],["A","A","B","B","C","C","D","D","E","E","F","F","G","G","H","H","I","I","J","J","K","K","L","L","M","M","N","N","O","O","P","P","Q","Q","R","R","S","S","T","T"],["NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES"],[2227,3458,4870,2707,2773,4750,2475,2122,4280,3293,3271,3521,2950,4159,4517,3988,2512,2799,4496,4425,4716,3547,3998,2827,2427,3989,2358,4197,2987,3130,2275,3597,3607,4499,2796,2193,4631,2492,4303,2233],[1134,1576,1510,1279,1224,581,1242,700,1529,624,1584,1471,202,1211,1726,1255,1855,616,1834,1953,987,1441,798,1542,550,1715,1100,1047,1777,1929,543,735,1688,1683,345,1601,1420,1333,1229,958],[1502,1327,1647,1188,1430,1768,806,1875,565,1024,528,1258,603,490,935,438,301,1751,1161,1276,1606,1665,376,783,1143,1560,1571,663,697,1596,726,1128,313,1410,1020,1444,1935,1816,1346,912],[0.39,0.02,0.19,0.29,0.54,0.03,0.04,0.36,0.47,0.38,0.69,0.65,0.46,0.2,0.26,0.77,0.86,0.59,0.22,0.34,0.63,0.83,0.89,0.42,0.94,0.45,0.95,0.58,0.01,0.28,0.32,0.96,0.07,0.76,0.13,0.05,0.85,0.75,0.31,0.23],[-0.02,0.01,0.28,0.12,0.32,0,-0.5,-0.01,0.27,0.24,-0.11,-0.4,-0.06,0.31,0.15,0.41,0.42,-0.05,-0.16,-0.48,0.18,-0.45,0.05,0.02,0.43,0.04,-0.46,-0.25,-0.14,0.37,0.16,-0.34,-0.32,0.44,0.26,-0.43,-0.13,-0.42,-0.09,-0.2]],"container":"<table class=\"display\">\n  <thead>\n    <tr>\n      <th> <\/th>\n      <th>type1<\/th>\n      <th>type2<\/th>\n      <th>value<\/th>\n      <th>value1<\/th>\n      <th>value2<\/th>\n      <th>prob1<\/th>\n      <th>prob2<\/th>\n    <\/tr>\n  <\/thead>\n<\/table>","options":{"pageLength":5,"dom":"ftip","columnDefs":[{"className":"dt-right","targets":[3,4,5,6,7]},{"orderable":false,"targets":0}],"order":[],"autoWidth":false,"orderClasses":false,"lengthMenu":[5,10,25,50,100]}},"evals":[],"jsHooks":[]}</script>

若是引入 htmltools 包中的函数，那么可以单独设置表格标题的 css 样式。如下，`caption-side: top` 表示表格标题的位置居于表格上方，`text-align: left` 表示文本对齐方式为居左，`font-size: 20px` 表示文本中字体大小为20px，`font-weight: bold` 表示文本中字体粗细为加粗。

``` r
datatable(
  data,
  caption = htmltools::tags$caption(
    style = 'caption-side: top; text-align: left; font-size: 20px; font-weight: bold;',
    '表1：一个表格的标题'))
```

<div id="htmlwidget-6" style="width:100%;height:auto;" class="datatables html-widget"></div>
<script type="application/json" data-for="htmlwidget-6">{"x":{"filter":"none","vertical":false,"caption":"<caption style=\"caption-side: top; text-align: left; font-size: 20px; font-weight: bold;\">表1：一个表格的标题<\/caption>","data":[["1","2","3","4","5","6","7","8","9","10","11","12","13","14","15","16","17","18","19","20","21","22","23","24","25","26","27","28","29","30","31","32","33","34","35","36","37","38","39","40"],["A","A","B","B","C","C","D","D","E","E","F","F","G","G","H","H","I","I","J","J","K","K","L","L","M","M","N","N","O","O","P","P","Q","Q","R","R","S","S","T","T"],["NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES"],[2227,3458,4870,2707,2773,4750,2475,2122,4280,3293,3271,3521,2950,4159,4517,3988,2512,2799,4496,4425,4716,3547,3998,2827,2427,3989,2358,4197,2987,3130,2275,3597,3607,4499,2796,2193,4631,2492,4303,2233],[1134,1576,1510,1279,1224,581,1242,700,1529,624,1584,1471,202,1211,1726,1255,1855,616,1834,1953,987,1441,798,1542,550,1715,1100,1047,1777,1929,543,735,1688,1683,345,1601,1420,1333,1229,958],[1502,1327,1647,1188,1430,1768,806,1875,565,1024,528,1258,603,490,935,438,301,1751,1161,1276,1606,1665,376,783,1143,1560,1571,663,697,1596,726,1128,313,1410,1020,1444,1935,1816,1346,912],[0.39,0.02,0.19,0.29,0.54,0.03,0.04,0.36,0.47,0.38,0.69,0.65,0.46,0.2,0.26,0.77,0.86,0.59,0.22,0.34,0.63,0.83,0.89,0.42,0.94,0.45,0.95,0.58,0.01,0.28,0.32,0.96,0.07,0.76,0.13,0.05,0.85,0.75,0.31,0.23],[-0.02,0.01,0.28,0.12,0.32,0,-0.5,-0.01,0.27,0.24,-0.11,-0.4,-0.06,0.31,0.15,0.41,0.42,-0.05,-0.16,-0.48,0.18,-0.45,0.05,0.02,0.43,0.04,-0.46,-0.25,-0.14,0.37,0.16,-0.34,-0.32,0.44,0.26,-0.43,-0.13,-0.42,-0.09,-0.2]],"container":"<table class=\"display\">\n  <thead>\n    <tr>\n      <th> <\/th>\n      <th>type1<\/th>\n      <th>type2<\/th>\n      <th>value<\/th>\n      <th>value1<\/th>\n      <th>value2<\/th>\n      <th>prob1<\/th>\n      <th>prob2<\/th>\n    <\/tr>\n  <\/thead>\n<\/table>","options":{"pageLength":5,"dom":"ftip","columnDefs":[{"className":"dt-right","targets":[3,4,5,6,7]},{"orderable":false,"targets":0}],"order":[],"autoWidth":false,"orderClasses":false,"lengthMenu":[5,10,25,50,100]}},"evals":[],"jsHooks":[]}</script>

当然，也可以一次引入多个 htmltools 包中的函数。如下，在`caption`参数中可以引入多级标题，并且分别设定单独的 css 样式。

``` r
datatable(
  data,
  caption = htmltools::tags$caption(
    style = 'caption-side: top; text-align: left;',
    htmltools::h5(class = 'font-size:20px;', '标题1：这是表格的主标题'),
    htmltools::h6(class = 'font-size:16px;', '标题2：这是表格的副标题')
  )
)
```

<div id="htmlwidget-7" style="width:100%;height:auto;" class="datatables html-widget"></div>
<script type="application/json" data-for="htmlwidget-7">{"x":{"filter":"none","vertical":false,"caption":"<caption style=\"caption-side: top; text-align: left;\">\n  <h5 class=\"font-size:20px;\">标题1：这是表格的主标题<\/h5>\n  <h6 class=\"font-size:16px;\">标题2：这是表格的副标题<\/h6>\n<\/caption>","data":[["1","2","3","4","5","6","7","8","9","10","11","12","13","14","15","16","17","18","19","20","21","22","23","24","25","26","27","28","29","30","31","32","33","34","35","36","37","38","39","40"],["A","A","B","B","C","C","D","D","E","E","F","F","G","G","H","H","I","I","J","J","K","K","L","L","M","M","N","N","O","O","P","P","Q","Q","R","R","S","S","T","T"],["NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES"],[2227,3458,4870,2707,2773,4750,2475,2122,4280,3293,3271,3521,2950,4159,4517,3988,2512,2799,4496,4425,4716,3547,3998,2827,2427,3989,2358,4197,2987,3130,2275,3597,3607,4499,2796,2193,4631,2492,4303,2233],[1134,1576,1510,1279,1224,581,1242,700,1529,624,1584,1471,202,1211,1726,1255,1855,616,1834,1953,987,1441,798,1542,550,1715,1100,1047,1777,1929,543,735,1688,1683,345,1601,1420,1333,1229,958],[1502,1327,1647,1188,1430,1768,806,1875,565,1024,528,1258,603,490,935,438,301,1751,1161,1276,1606,1665,376,783,1143,1560,1571,663,697,1596,726,1128,313,1410,1020,1444,1935,1816,1346,912],[0.39,0.02,0.19,0.29,0.54,0.03,0.04,0.36,0.47,0.38,0.69,0.65,0.46,0.2,0.26,0.77,0.86,0.59,0.22,0.34,0.63,0.83,0.89,0.42,0.94,0.45,0.95,0.58,0.01,0.28,0.32,0.96,0.07,0.76,0.13,0.05,0.85,0.75,0.31,0.23],[-0.02,0.01,0.28,0.12,0.32,0,-0.5,-0.01,0.27,0.24,-0.11,-0.4,-0.06,0.31,0.15,0.41,0.42,-0.05,-0.16,-0.48,0.18,-0.45,0.05,0.02,0.43,0.04,-0.46,-0.25,-0.14,0.37,0.16,-0.34,-0.32,0.44,0.26,-0.43,-0.13,-0.42,-0.09,-0.2]],"container":"<table class=\"display\">\n  <thead>\n    <tr>\n      <th> <\/th>\n      <th>type1<\/th>\n      <th>type2<\/th>\n      <th>value<\/th>\n      <th>value1<\/th>\n      <th>value2<\/th>\n      <th>prob1<\/th>\n      <th>prob2<\/th>\n    <\/tr>\n  <\/thead>\n<\/table>","options":{"pageLength":5,"dom":"ftip","columnDefs":[{"className":"dt-right","targets":[3,4,5,6,7]},{"orderable":false,"targets":0}],"order":[],"autoWidth":false,"orderClasses":false,"lengthMenu":[5,10,25,50,100]}},"evals":[],"jsHooks":[]}</script>

#### 1.2.1.2.表格脚注

表格脚注，也可称为尾注，位置通常在表格的下方。设定脚注也可以使用 caption 参数来实现，区别就是设置 `caption-side: bottom`，即标题的位置挪到表格下方。

``` r
datatable(
  data,
  caption = htmltools::tags$caption(style =
                                    'caption-side: bottom; text-align: left; color: red;',
                                    '注1：一个表格的脚注'))
```

<div id="htmlwidget-8" style="width:100%;height:auto;" class="datatables html-widget"></div>
<script type="application/json" data-for="htmlwidget-8">{"x":{"filter":"none","vertical":false,"caption":"<caption style=\"caption-side: bottom; text-align: left; color: red;\">注1：一个表格的脚注<\/caption>","data":[["1","2","3","4","5","6","7","8","9","10","11","12","13","14","15","16","17","18","19","20","21","22","23","24","25","26","27","28","29","30","31","32","33","34","35","36","37","38","39","40"],["A","A","B","B","C","C","D","D","E","E","F","F","G","G","H","H","I","I","J","J","K","K","L","L","M","M","N","N","O","O","P","P","Q","Q","R","R","S","S","T","T"],["NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES"],[2227,3458,4870,2707,2773,4750,2475,2122,4280,3293,3271,3521,2950,4159,4517,3988,2512,2799,4496,4425,4716,3547,3998,2827,2427,3989,2358,4197,2987,3130,2275,3597,3607,4499,2796,2193,4631,2492,4303,2233],[1134,1576,1510,1279,1224,581,1242,700,1529,624,1584,1471,202,1211,1726,1255,1855,616,1834,1953,987,1441,798,1542,550,1715,1100,1047,1777,1929,543,735,1688,1683,345,1601,1420,1333,1229,958],[1502,1327,1647,1188,1430,1768,806,1875,565,1024,528,1258,603,490,935,438,301,1751,1161,1276,1606,1665,376,783,1143,1560,1571,663,697,1596,726,1128,313,1410,1020,1444,1935,1816,1346,912],[0.39,0.02,0.19,0.29,0.54,0.03,0.04,0.36,0.47,0.38,0.69,0.65,0.46,0.2,0.26,0.77,0.86,0.59,0.22,0.34,0.63,0.83,0.89,0.42,0.94,0.45,0.95,0.58,0.01,0.28,0.32,0.96,0.07,0.76,0.13,0.05,0.85,0.75,0.31,0.23],[-0.02,0.01,0.28,0.12,0.32,0,-0.5,-0.01,0.27,0.24,-0.11,-0.4,-0.06,0.31,0.15,0.41,0.42,-0.05,-0.16,-0.48,0.18,-0.45,0.05,0.02,0.43,0.04,-0.46,-0.25,-0.14,0.37,0.16,-0.34,-0.32,0.44,0.26,-0.43,-0.13,-0.42,-0.09,-0.2]],"container":"<table class=\"display\">\n  <thead>\n    <tr>\n      <th> <\/th>\n      <th>type1<\/th>\n      <th>type2<\/th>\n      <th>value<\/th>\n      <th>value1<\/th>\n      <th>value2<\/th>\n      <th>prob1<\/th>\n      <th>prob2<\/th>\n    <\/tr>\n  <\/thead>\n<\/table>","options":{"pageLength":5,"dom":"ftip","columnDefs":[{"className":"dt-right","targets":[3,4,5,6,7]},{"orderable":false,"targets":0}],"order":[],"autoWidth":false,"orderClasses":false,"lengthMenu":[5,10,25,50,100]}},"evals":[],"jsHooks":[]}</script>

基于 htmltools 可以嵌套多层的特点，也可以填入多行脚注。

``` r
datatable(
  data,
  caption = htmltools::tags$caption(
    style = 'caption-side: bottom; text-align: left; line-height: 60%; color: red;',
    htmltools::p(class = 'font-size:14px;', '注1：数据来源'),
    htmltools::p(class = 'font-size:14px;', '注2：其他说明')
  )
)
```

<div id="htmlwidget-9" style="width:100%;height:auto;" class="datatables html-widget"></div>
<script type="application/json" data-for="htmlwidget-9">{"x":{"filter":"none","vertical":false,"caption":"<caption style=\"caption-side: bottom; text-align: left; line-height: 60%; color: red;\">\n  <p class=\"font-size:14px;\">注1：数据来源<\/p>\n  <p class=\"font-size:14px;\">注2：其他说明<\/p>\n<\/caption>","data":[["1","2","3","4","5","6","7","8","9","10","11","12","13","14","15","16","17","18","19","20","21","22","23","24","25","26","27","28","29","30","31","32","33","34","35","36","37","38","39","40"],["A","A","B","B","C","C","D","D","E","E","F","F","G","G","H","H","I","I","J","J","K","K","L","L","M","M","N","N","O","O","P","P","Q","Q","R","R","S","S","T","T"],["NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES"],[2227,3458,4870,2707,2773,4750,2475,2122,4280,3293,3271,3521,2950,4159,4517,3988,2512,2799,4496,4425,4716,3547,3998,2827,2427,3989,2358,4197,2987,3130,2275,3597,3607,4499,2796,2193,4631,2492,4303,2233],[1134,1576,1510,1279,1224,581,1242,700,1529,624,1584,1471,202,1211,1726,1255,1855,616,1834,1953,987,1441,798,1542,550,1715,1100,1047,1777,1929,543,735,1688,1683,345,1601,1420,1333,1229,958],[1502,1327,1647,1188,1430,1768,806,1875,565,1024,528,1258,603,490,935,438,301,1751,1161,1276,1606,1665,376,783,1143,1560,1571,663,697,1596,726,1128,313,1410,1020,1444,1935,1816,1346,912],[0.39,0.02,0.19,0.29,0.54,0.03,0.04,0.36,0.47,0.38,0.69,0.65,0.46,0.2,0.26,0.77,0.86,0.59,0.22,0.34,0.63,0.83,0.89,0.42,0.94,0.45,0.95,0.58,0.01,0.28,0.32,0.96,0.07,0.76,0.13,0.05,0.85,0.75,0.31,0.23],[-0.02,0.01,0.28,0.12,0.32,0,-0.5,-0.01,0.27,0.24,-0.11,-0.4,-0.06,0.31,0.15,0.41,0.42,-0.05,-0.16,-0.48,0.18,-0.45,0.05,0.02,0.43,0.04,-0.46,-0.25,-0.14,0.37,0.16,-0.34,-0.32,0.44,0.26,-0.43,-0.13,-0.42,-0.09,-0.2]],"container":"<table class=\"display\">\n  <thead>\n    <tr>\n      <th> <\/th>\n      <th>type1<\/th>\n      <th>type2<\/th>\n      <th>value<\/th>\n      <th>value1<\/th>\n      <th>value2<\/th>\n      <th>prob1<\/th>\n      <th>prob2<\/th>\n    <\/tr>\n  <\/thead>\n<\/table>","options":{"pageLength":5,"dom":"ftip","columnDefs":[{"className":"dt-right","targets":[3,4,5,6,7]},{"orderable":false,"targets":0}],"order":[],"autoWidth":false,"orderClasses":false,"lengthMenu":[5,10,25,50,100]}},"evals":[],"jsHooks":[]}</script>

#### 1.2.1.3.其他

也可以尝试通过 htmltools 引入其他 html 表格元素，前提是需要对想要引入的元素有点了解，一个简单的例子如下。

``` r
datatable(data,
          caption = htmltools::withTags(table(thead('页眉：这里写页眉'))))
```

<div id="htmlwidget-10" style="width:100%;height:auto;" class="datatables html-widget"></div>
<script type="application/json" data-for="htmlwidget-10">{"x":{"filter":"none","vertical":false,"caption":"<table>\n  <thead>页眉：这里写页眉<\/thead>\n<\/table>","data":[["1","2","3","4","5","6","7","8","9","10","11","12","13","14","15","16","17","18","19","20","21","22","23","24","25","26","27","28","29","30","31","32","33","34","35","36","37","38","39","40"],["A","A","B","B","C","C","D","D","E","E","F","F","G","G","H","H","I","I","J","J","K","K","L","L","M","M","N","N","O","O","P","P","Q","Q","R","R","S","S","T","T"],["NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES"],[2227,3458,4870,2707,2773,4750,2475,2122,4280,3293,3271,3521,2950,4159,4517,3988,2512,2799,4496,4425,4716,3547,3998,2827,2427,3989,2358,4197,2987,3130,2275,3597,3607,4499,2796,2193,4631,2492,4303,2233],[1134,1576,1510,1279,1224,581,1242,700,1529,624,1584,1471,202,1211,1726,1255,1855,616,1834,1953,987,1441,798,1542,550,1715,1100,1047,1777,1929,543,735,1688,1683,345,1601,1420,1333,1229,958],[1502,1327,1647,1188,1430,1768,806,1875,565,1024,528,1258,603,490,935,438,301,1751,1161,1276,1606,1665,376,783,1143,1560,1571,663,697,1596,726,1128,313,1410,1020,1444,1935,1816,1346,912],[0.39,0.02,0.19,0.29,0.54,0.03,0.04,0.36,0.47,0.38,0.69,0.65,0.46,0.2,0.26,0.77,0.86,0.59,0.22,0.34,0.63,0.83,0.89,0.42,0.94,0.45,0.95,0.58,0.01,0.28,0.32,0.96,0.07,0.76,0.13,0.05,0.85,0.75,0.31,0.23],[-0.02,0.01,0.28,0.12,0.32,0,-0.5,-0.01,0.27,0.24,-0.11,-0.4,-0.06,0.31,0.15,0.41,0.42,-0.05,-0.16,-0.48,0.18,-0.45,0.05,0.02,0.43,0.04,-0.46,-0.25,-0.14,0.37,0.16,-0.34,-0.32,0.44,0.26,-0.43,-0.13,-0.42,-0.09,-0.2]],"container":"<table class=\"display\">\n  <thead>\n    <tr>\n      <th> <\/th>\n      <th>type1<\/th>\n      <th>type2<\/th>\n      <th>value<\/th>\n      <th>value1<\/th>\n      <th>value2<\/th>\n      <th>prob1<\/th>\n      <th>prob2<\/th>\n    <\/tr>\n  <\/thead>\n<\/table>","options":{"pageLength":5,"dom":"ftip","columnDefs":[{"className":"dt-right","targets":[3,4,5,6,7]},{"orderable":false,"targets":0}],"order":[],"autoWidth":false,"orderClasses":false,"lengthMenu":[5,10,25,50,100]}},"evals":[],"jsHooks":[]}</script>

### 1.2.2.从表格容器（container）中引入

从表格容器（container）中引入 htmltools，相当于在 R 里面写[纯纯的 html](https://www.w3school.com.cn/html/html_tables.asp)。若是对 html 中的表格元素比较熟悉，直接写好整个表格的框架和样式也可以。

|  html 元素   |     英文全称      |         描述         | 对应 htmltools 包函数 |
|:------------:|:-----------------:|:--------------------:|:---------------------:|
|  `<table>`   |       table       |       定义表格       |       `table()`       |
|    `<th>`    | table header cell | 定义表格表头的单元格 |        `th()`         |
|    `<tr>`    |     table row     |     定义表格的行     |        `tr()`         |
|    `<td>`    |  table data cell  | 定义表格主体的单元格 |        `td()`         |
| `<caption>`  |      caption      |    定义表格的标题    |      `caption()`      |
| `<colgroup>` |   column group    |    定义表格列的组    |          \-           |
|   `<col>`    |      column       |   定义表格列的属性   |          \-           |
|  `<thead>`   |    table head     |    定义表格的表头    |       `thead()`       |
|  `<tbody>`   |    table body     |    定义表格的主体    |       `tbody()`       |
|  `<tfoot>`   |    table foot     |    定义表格的脚注    |       `tfoot()`       |

#### 1.2.2.1.多行表头

如下，`thead()` 定义表格的表头；`tr()` 定义表格的行，那么 `thead(tr())` 定义表格表头中的行；`th()` 定义表格表头中的单元格，那么 `thead(tr(th()))` 定义表格表头中一行的一个单元格。需要定义多少行表头，则需要写多少个 `tr()`，一行表头中有多少单元格则需要写多少个 `th()`。其中， 参数 rowspan 用于设置单元格可横跨的行数，参数 colspan 用于设置单元格可横跨的列数。

``` r
table.header = htmltools::withTags(table(thead(
  tr(
    th(rowspan = 2, colspan = 1, '客户范围'),
    th(rowspan = 2, colspan = 1, '有无'),
    th(rowspan = 2, colspan = 1, '总客户数'),
    th(rowspan = 1, colspan = 2, '复购'),
    th(rowspan = 1, colspan = 2, '留存')
  ),
  tr(
    th(rowspan = 1, colspan = 1, '复购人数'),
    th(rowspan = 1, colspan = 1, '复购比例'),
    th(rowspan = 1, colspan = 1, '留存人数'),
    th(rowspan = 1, colspan = 1, '留存比例')
  )
)))

datatable(
  data[, c(1:4, 6, 5, 7)],
  container = table.header,
  options = list(dom = 'tip'),
  rownames = FALSE)
```

<div id="htmlwidget-11" style="width:100%;height:auto;" class="datatables html-widget"></div>
<script type="application/json" data-for="htmlwidget-11">{"x":{"filter":"none","vertical":false,"class":"display","data":[["A","A","B","B","C","C","D","D","E","E","F","F","G","G","H","H","I","I","J","J","K","K","L","L","M","M","N","N","O","O","P","P","Q","Q","R","R","S","S","T","T"],["NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES"],[2227,3458,4870,2707,2773,4750,2475,2122,4280,3293,3271,3521,2950,4159,4517,3988,2512,2799,4496,4425,4716,3547,3998,2827,2427,3989,2358,4197,2987,3130,2275,3597,3607,4499,2796,2193,4631,2492,4303,2233],[1134,1576,1510,1279,1224,581,1242,700,1529,624,1584,1471,202,1211,1726,1255,1855,616,1834,1953,987,1441,798,1542,550,1715,1100,1047,1777,1929,543,735,1688,1683,345,1601,1420,1333,1229,958],[0.39,0.02,0.19,0.29,0.54,0.03,0.04,0.36,0.47,0.38,0.69,0.65,0.46,0.2,0.26,0.77,0.86,0.59,0.22,0.34,0.63,0.83,0.89,0.42,0.94,0.45,0.95,0.58,0.01,0.28,0.32,0.96,0.07,0.76,0.13,0.05,0.85,0.75,0.31,0.23],[1502,1327,1647,1188,1430,1768,806,1875,565,1024,528,1258,603,490,935,438,301,1751,1161,1276,1606,1665,376,783,1143,1560,1571,663,697,1596,726,1128,313,1410,1020,1444,1935,1816,1346,912],[-0.02,0.01,0.28,0.12,0.32,0,-0.5,-0.01,0.27,0.24,-0.11,-0.4,-0.06,0.31,0.15,0.41,0.42,-0.05,-0.16,-0.48,0.18,-0.45,0.05,0.02,0.43,0.04,-0.46,-0.25,-0.14,0.37,0.16,-0.34,-0.32,0.44,0.26,-0.43,-0.13,-0.42,-0.09,-0.2]],"container":"<table>\n  <thead>\n    <tr>\n      <th rowspan=\"2\" colspan=\"1\">客户范围<\/th>\n      <th rowspan=\"2\" colspan=\"1\">有无<\/th>\n      <th rowspan=\"2\" colspan=\"1\">总客户数<\/th>\n      <th rowspan=\"1\" colspan=\"2\">复购<\/th>\n      <th rowspan=\"1\" colspan=\"2\">留存<\/th>\n    <\/tr>\n    <tr>\n      <th rowspan=\"1\" colspan=\"1\">复购人数<\/th>\n      <th rowspan=\"1\" colspan=\"1\">复购比例<\/th>\n      <th rowspan=\"1\" colspan=\"1\">留存人数<\/th>\n      <th rowspan=\"1\" colspan=\"1\">留存比例<\/th>\n    <\/tr>\n  <\/thead>\n<\/table>","options":{"pageLength":5,"dom":"tip","columnDefs":[{"className":"dt-right","targets":[2,3,4,5,6]}],"order":[],"autoWidth":false,"orderClasses":false,"lengthMenu":[5,10,25,50,100]}},"evals":[],"jsHooks":[]}</script>

#### 1.2.2.2.标题、脚注

表格容器里也可以直接添加表格标题、脚注，并且可以分别为标题、脚注引入预先定义好的 css 样式。

``` css
.top{
caption-side: top;
text-align:left;
}

.bottom{
caption-side: bottom;
text-align:left;
line-height:60%;
}
```

<style type="text/css">
.top{
caption-side: top;
text-align:left;
}

.bottom{
caption-side: bottom;
text-align:left;
line-height:60%;
}
</style>

``` r
sketch = htmltools::withTags(table(
  caption(class = 'top', h5('主标题：这里写主标题'), h6('副标题：这里写副标题')),
  caption(class = 'bottom', h6('注1：数据来源'), h6('注2：其他说明')),
  thead(tr(
    th('第1列'),
    th('第2列'),
    th('第3列'),
    th('第4列'),
    th('第5列'),
    th('第6列'),
    th('第7列')
  )),
  tfoot(tr(
    th('第1列 结尾'),
    th('第2列 结尾'),
    th('第3列 结尾'),
    th('第4列 结尾'),
    th('第5列 结尾'),
    th('第6列 结尾'),
    th('第7列 结尾')
  ))
))

datatable(
  data,
  container = sketch,
  options = list(dom = 'tip'),
  rownames = FALSE
)
```

<div id="htmlwidget-12" style="width:100%;height:auto;" class="datatables html-widget"></div>
<script type="application/json" data-for="htmlwidget-12">{"x":{"filter":"none","vertical":false,"class":"display","data":[["A","A","B","B","C","C","D","D","E","E","F","F","G","G","H","H","I","I","J","J","K","K","L","L","M","M","N","N","O","O","P","P","Q","Q","R","R","S","S","T","T"],["NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES"],[2227,3458,4870,2707,2773,4750,2475,2122,4280,3293,3271,3521,2950,4159,4517,3988,2512,2799,4496,4425,4716,3547,3998,2827,2427,3989,2358,4197,2987,3130,2275,3597,3607,4499,2796,2193,4631,2492,4303,2233],[1134,1576,1510,1279,1224,581,1242,700,1529,624,1584,1471,202,1211,1726,1255,1855,616,1834,1953,987,1441,798,1542,550,1715,1100,1047,1777,1929,543,735,1688,1683,345,1601,1420,1333,1229,958],[1502,1327,1647,1188,1430,1768,806,1875,565,1024,528,1258,603,490,935,438,301,1751,1161,1276,1606,1665,376,783,1143,1560,1571,663,697,1596,726,1128,313,1410,1020,1444,1935,1816,1346,912],[0.39,0.02,0.19,0.29,0.54,0.03,0.04,0.36,0.47,0.38,0.69,0.65,0.46,0.2,0.26,0.77,0.86,0.59,0.22,0.34,0.63,0.83,0.89,0.42,0.94,0.45,0.95,0.58,0.01,0.28,0.32,0.96,0.07,0.76,0.13,0.05,0.85,0.75,0.31,0.23],[-0.02,0.01,0.28,0.12,0.32,0,-0.5,-0.01,0.27,0.24,-0.11,-0.4,-0.06,0.31,0.15,0.41,0.42,-0.05,-0.16,-0.48,0.18,-0.45,0.05,0.02,0.43,0.04,-0.46,-0.25,-0.14,0.37,0.16,-0.34,-0.32,0.44,0.26,-0.43,-0.13,-0.42,-0.09,-0.2]],"container":"<table>\n  <caption class=\"top\">\n    <h5>主标题：这里写主标题<\/h5>\n    <h6>副标题：这里写副标题<\/h6>\n  <\/caption>\n  <caption class=\"bottom\">\n    <h6>注1：数据来源<\/h6>\n    <h6>注2：其他说明<\/h6>\n  <\/caption>\n  <thead>\n    <tr>\n      <th>第1列<\/th>\n      <th>第2列<\/th>\n      <th>第3列<\/th>\n      <th>第4列<\/th>\n      <th>第5列<\/th>\n      <th>第6列<\/th>\n      <th>第7列<\/th>\n    <\/tr>\n  <\/thead>\n  <tfoot>\n    <tr>\n      <th>第1列 结尾<\/th>\n      <th>第2列 结尾<\/th>\n      <th>第3列 结尾<\/th>\n      <th>第4列 结尾<\/th>\n      <th>第5列 结尾<\/th>\n      <th>第6列 结尾<\/th>\n      <th>第7列 结尾<\/th>\n    <\/tr>\n  <\/tfoot>\n<\/table>","options":{"pageLength":5,"dom":"tip","columnDefs":[{"className":"dt-right","targets":[2,3,4,5,6]}],"order":[],"autoWidth":false,"orderClasses":false,"lengthMenu":[5,10,25,50,100]}},"evals":[],"jsHooks":[]}</script>

### 1.2.3.把表格放在 div 块中

前面两个小节是在表格中引入 htmltools，从而丰富表格元素。也可以换个思路，把表格引入到 htmltools 中，同样也可以引入预先设定好的 css 样式。使用此方法须对 html 元素有少量理解，比如多个 div 框嵌套时，须注意父 div 框和子 div 框之间的元素属性继承问题。

``` css
.table {
  font-size: 12px;
  line-height: 90%;
}

.title {
  font-size: 14px;
  font-weight: bold;
}
```

<style type="text/css">
.table {
  font-size: 12px;
  line-height: 90%;
}

.title {
  font-size: 14px;
  font-weight: bold;
}
</style>

``` r
tbl <- datatable(data,
                 options = list(dom = 'tip'))

htmltools::div(
  class = "table",
  htmltools::div(class = "title",
                 "主标题：这是表格的主标题",
                 htmltools::h6("副标题：这是表格的副标题")),
  tbl,
  htmltools::div(class = "title", "脚注：这是表格的脚注", htmltools::h6("脚注：这也可是表格的脚注"))
)
```

<div class="table">
<div class="title">
主标题：这是表格的主标题
<h6>副标题：这是表格的副标题</h6>
</div>
<div id="htmlwidget-13" style="width:100%;height:auto;" class="datatables html-widget"></div>
<script type="application/json" data-for="htmlwidget-13">{"x":{"filter":"none","vertical":false,"data":[["1","2","3","4","5","6","7","8","9","10","11","12","13","14","15","16","17","18","19","20","21","22","23","24","25","26","27","28","29","30","31","32","33","34","35","36","37","38","39","40"],["A","A","B","B","C","C","D","D","E","E","F","F","G","G","H","H","I","I","J","J","K","K","L","L","M","M","N","N","O","O","P","P","Q","Q","R","R","S","S","T","T"],["NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES"],[2227,3458,4870,2707,2773,4750,2475,2122,4280,3293,3271,3521,2950,4159,4517,3988,2512,2799,4496,4425,4716,3547,3998,2827,2427,3989,2358,4197,2987,3130,2275,3597,3607,4499,2796,2193,4631,2492,4303,2233],[1134,1576,1510,1279,1224,581,1242,700,1529,624,1584,1471,202,1211,1726,1255,1855,616,1834,1953,987,1441,798,1542,550,1715,1100,1047,1777,1929,543,735,1688,1683,345,1601,1420,1333,1229,958],[1502,1327,1647,1188,1430,1768,806,1875,565,1024,528,1258,603,490,935,438,301,1751,1161,1276,1606,1665,376,783,1143,1560,1571,663,697,1596,726,1128,313,1410,1020,1444,1935,1816,1346,912],[0.39,0.02,0.19,0.29,0.54,0.03,0.04,0.36,0.47,0.38,0.69,0.65,0.46,0.2,0.26,0.77,0.86,0.59,0.22,0.34,0.63,0.83,0.89,0.42,0.94,0.45,0.95,0.58,0.01,0.28,0.32,0.96,0.07,0.76,0.13,0.05,0.85,0.75,0.31,0.23],[-0.02,0.01,0.28,0.12,0.32,0,-0.5,-0.01,0.27,0.24,-0.11,-0.4,-0.06,0.31,0.15,0.41,0.42,-0.05,-0.16,-0.48,0.18,-0.45,0.05,0.02,0.43,0.04,-0.46,-0.25,-0.14,0.37,0.16,-0.34,-0.32,0.44,0.26,-0.43,-0.13,-0.42,-0.09,-0.2]],"container":"<table class=\"display\">\n  <thead>\n    <tr>\n      <th> <\/th>\n      <th>type1<\/th>\n      <th>type2<\/th>\n      <th>value<\/th>\n      <th>value1<\/th>\n      <th>value2<\/th>\n      <th>prob1<\/th>\n      <th>prob2<\/th>\n    <\/tr>\n  <\/thead>\n<\/table>","options":{"pageLength":5,"dom":"tip","columnDefs":[{"className":"dt-right","targets":[3,4,5,6,7]},{"orderable":false,"targets":0}],"order":[],"autoWidth":false,"orderClasses":false,"lengthMenu":[5,10,25,50,100]}},"evals":[],"jsHooks":[]}</script>
<div class="title">
脚注：这是表格的脚注
<h6>脚注：这也可是表格的脚注</h6>
</div>
</div>

## 1.3.通过 class/className 参数设置样式

### 1.3.1.表格主体的默认样式

DT 包继承了 DataTables 的[默认样式](https://datatables.net/manual/styling/classes#Table-classes)，可以使用以下类名的任意组合来构建所需的表格样式。虽然本章节的章节名是“静态样式”，但由于 DataTables 本身是用于展现动态表格的，因此默认样式实际上是各种动态样式。

|    类别名    |                                            描述                                             |
|:------------:|:-------------------------------------------------------------------------------------------:|
|   display    |                        stripe、hover、row-border、order-column的简写                        |
| cell-border  |                               每个单元格的所有四个边都有边框                                |
|   compact    |                减少 DataTable 使用的默认样式的空白数量，增加屏幕上的信息密度                |
|    hover     |                                    鼠标悬停时突出显示行                                     |
|    nowrap    |                   禁用表格中内容的换行，因此单元格中的所有文本都在一行上                    |
| order-column |                                 突出显示当前排序表数据的列                                  |
|  row-border  | 仅围绕每个顶部和底部的边框（即用于行）。注意cell-border和row-border是互斥的，不能一起使用。 |
|    stripe    |                                          行条带化                                           |

### 1.3.2.表格单元格的默认样式

DT 中的单元格默认样式仅有文本对齐和排序。其中，文本对齐方式可以分别对表格的表头（head）和表格主体（body）单独设置。若类名中不写 head 或 body，如`className = 'dt-center'`表示将目标列的表头和单元格的文本对齐方式均设置为居中。`className= ''`中可以写入多个类名。

|           类名            |      描述      |
|:-------------------------:|:--------------:|
|  `dt[-head|-body]-left`   |   左对齐文本   |
| `dt[-head|-body]-center`  | 居中对齐的文本 |
|  `dt[-head|-body]-right`  |   右对齐文本   |
| `dt[-head|-body]-justify` | 两端对齐的文本 |
| `dt[-head|-body]-nowrap`  |   强制不换行   |

``` r
datatable(data,
          options = list(columnDefs = list(
            # 设置目标列表头文本居右，单元格文本居左
            list(targets = 5, className = 'dt-head-right dt-body-left'),
            # 设置目标列的表头、单元格文本均居中
            list(targets = c(6, 7), className = 'dt-center')
          )))
```

<div id="htmlwidget-14" style="width:100%;height:auto;" class="datatables html-widget"></div>
<script type="application/json" data-for="htmlwidget-14">{"x":{"filter":"none","vertical":false,"data":[["1","2","3","4","5","6","7","8","9","10","11","12","13","14","15","16","17","18","19","20","21","22","23","24","25","26","27","28","29","30","31","32","33","34","35","36","37","38","39","40"],["A","A","B","B","C","C","D","D","E","E","F","F","G","G","H","H","I","I","J","J","K","K","L","L","M","M","N","N","O","O","P","P","Q","Q","R","R","S","S","T","T"],["NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES"],[2227,3458,4870,2707,2773,4750,2475,2122,4280,3293,3271,3521,2950,4159,4517,3988,2512,2799,4496,4425,4716,3547,3998,2827,2427,3989,2358,4197,2987,3130,2275,3597,3607,4499,2796,2193,4631,2492,4303,2233],[1134,1576,1510,1279,1224,581,1242,700,1529,624,1584,1471,202,1211,1726,1255,1855,616,1834,1953,987,1441,798,1542,550,1715,1100,1047,1777,1929,543,735,1688,1683,345,1601,1420,1333,1229,958],[1502,1327,1647,1188,1430,1768,806,1875,565,1024,528,1258,603,490,935,438,301,1751,1161,1276,1606,1665,376,783,1143,1560,1571,663,697,1596,726,1128,313,1410,1020,1444,1935,1816,1346,912],[0.39,0.02,0.19,0.29,0.54,0.03,0.04,0.36,0.47,0.38,0.69,0.65,0.46,0.2,0.26,0.77,0.86,0.59,0.22,0.34,0.63,0.83,0.89,0.42,0.94,0.45,0.95,0.58,0.01,0.28,0.32,0.96,0.07,0.76,0.13,0.05,0.85,0.75,0.31,0.23],[-0.02,0.01,0.28,0.12,0.32,0,-0.5,-0.01,0.27,0.24,-0.11,-0.4,-0.06,0.31,0.15,0.41,0.42,-0.05,-0.16,-0.48,0.18,-0.45,0.05,0.02,0.43,0.04,-0.46,-0.25,-0.14,0.37,0.16,-0.34,-0.32,0.44,0.26,-0.43,-0.13,-0.42,-0.09,-0.2]],"container":"<table class=\"display\">\n  <thead>\n    <tr>\n      <th> <\/th>\n      <th>type1<\/th>\n      <th>type2<\/th>\n      <th>value<\/th>\n      <th>value1<\/th>\n      <th>value2<\/th>\n      <th>prob1<\/th>\n      <th>prob2<\/th>\n    <\/tr>\n  <\/thead>\n<\/table>","options":{"pageLength":5,"dom":"ftip","columnDefs":[{"targets":5,"className":"dt-head-right dt-body-left"},{"targets":[6,7],"className":"dt-center"},{"className":"dt-right","targets":[3,4]},{"orderable":false,"targets":0}],"order":[],"autoWidth":false,"orderClasses":false,"lengthMenu":[5,10,25,50,100]}},"evals":[],"jsHooks":[]}</script>

### 1.3.3.自定义 css 样式（class/className）

除了可以使用默认样式以外，还可以设置自定义样式，方法是先定义好 css 样式的类名和具体样式属性，然后用`calss = '类名'`的方式引入。有几点需要特别注意：

-   其一，一般情况下，这种方法引入的 css 样式会同时改变目标列的表头和单元格的样式。

-   其二，DT 包本身有默认的文本对齐样式，可能会与自定义的 css 样式产生冲突。

如下，定义了两个 css 样式，类名 ‘border-left’ 表示为目标列的左边框增加一条黑色实线，且文本对齐方式为居中；类名 ‘color’ 表示设定目标列字体颜色为红色，且文本对齐方式为居中。显然，对目标列左边框线和列宽度的设定起了作用，但文本对齐方式没有改变，这是由于 DataTables 自带的文本对齐方式设定地[更加详细](https://github.com/DataTables/DataTablesSrc/blob/fe28d4/css/typography.scss)，而自定义的样式设定地[更加简略](https://d.cosx.org/d/423692-dt-bao-she-zhi-zi-ding-yi-css-yang-shi-shi-wen-ben-ju-zhong-bu-qi-zuo-yong/2)，于是后者设定的文本对齐方式被前者覆盖，从而不起作用。

``` css
.border-left {
  border-left: 1px solid #555;
  text-align: center;
}

.color {
  color: red;
  text-align: center;
}
```

<style type="text/css">
.border-left {
  border-left: 1px solid #555;
  text-align: center;
}

.color {
  color: red;
  text-align: center;
}
</style>

``` r
datatable(data, options = list(columnDefs = list(
  list(targets = 3, class = 'border-left'),
  list(targets = 4, class = 'color')
)))
```

<div id="htmlwidget-15" style="width:100%;height:auto;" class="datatables html-widget"></div>
<script type="application/json" data-for="htmlwidget-15">{"x":{"filter":"none","vertical":false,"data":[["1","2","3","4","5","6","7","8","9","10","11","12","13","14","15","16","17","18","19","20","21","22","23","24","25","26","27","28","29","30","31","32","33","34","35","36","37","38","39","40"],["A","A","B","B","C","C","D","D","E","E","F","F","G","G","H","H","I","I","J","J","K","K","L","L","M","M","N","N","O","O","P","P","Q","Q","R","R","S","S","T","T"],["NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES"],[2227,3458,4870,2707,2773,4750,2475,2122,4280,3293,3271,3521,2950,4159,4517,3988,2512,2799,4496,4425,4716,3547,3998,2827,2427,3989,2358,4197,2987,3130,2275,3597,3607,4499,2796,2193,4631,2492,4303,2233],[1134,1576,1510,1279,1224,581,1242,700,1529,624,1584,1471,202,1211,1726,1255,1855,616,1834,1953,987,1441,798,1542,550,1715,1100,1047,1777,1929,543,735,1688,1683,345,1601,1420,1333,1229,958],[1502,1327,1647,1188,1430,1768,806,1875,565,1024,528,1258,603,490,935,438,301,1751,1161,1276,1606,1665,376,783,1143,1560,1571,663,697,1596,726,1128,313,1410,1020,1444,1935,1816,1346,912],[0.39,0.02,0.19,0.29,0.54,0.03,0.04,0.36,0.47,0.38,0.69,0.65,0.46,0.2,0.26,0.77,0.86,0.59,0.22,0.34,0.63,0.83,0.89,0.42,0.94,0.45,0.95,0.58,0.01,0.28,0.32,0.96,0.07,0.76,0.13,0.05,0.85,0.75,0.31,0.23],[-0.02,0.01,0.28,0.12,0.32,0,-0.5,-0.01,0.27,0.24,-0.11,-0.4,-0.06,0.31,0.15,0.41,0.42,-0.05,-0.16,-0.48,0.18,-0.45,0.05,0.02,0.43,0.04,-0.46,-0.25,-0.14,0.37,0.16,-0.34,-0.32,0.44,0.26,-0.43,-0.13,-0.42,-0.09,-0.2]],"container":"<table class=\"display\">\n  <thead>\n    <tr>\n      <th> <\/th>\n      <th>type1<\/th>\n      <th>type2<\/th>\n      <th>value<\/th>\n      <th>value1<\/th>\n      <th>value2<\/th>\n      <th>prob1<\/th>\n      <th>prob2<\/th>\n    <\/tr>\n  <\/thead>\n<\/table>","options":{"pageLength":5,"dom":"ftip","columnDefs":[{"targets":3,"class":"border-left"},{"targets":4,"class":"color"},{"className":"dt-right","targets":[3,4,5,6,7]},{"orderable":false,"targets":0}],"order":[],"autoWidth":false,"orderClasses":false,"lengthMenu":[5,10,25,50,100]}},"evals":[],"jsHooks":[]}</script>

此时，若要使目标列的文本对齐方式变成居中，有两种方法可以实现，一是自定义的样式参照 DataTables 设定地更加详细，二是在`class= ''`中也添加默认样式。

``` css
table.dataTable th.border-left-new, table.dataTable td.border-left-new {
  border-left: 1px solid #555;
  text-align: center;
}
```

<style type="text/css">
table.dataTable th.border-left-new, table.dataTable td.border-left-new {
  border-left: 1px solid #555;
  text-align: center;
}
</style>

``` r
datatable(data, options = list(columnDefs = list(
  # 方法一
  list(targets = 3, class = 'border-left-new'),
  # 方法二
  list(targets = 4, class = 'dt-center color')
)))
```

<div id="htmlwidget-16" style="width:100%;height:auto;" class="datatables html-widget"></div>
<script type="application/json" data-for="htmlwidget-16">{"x":{"filter":"none","vertical":false,"data":[["1","2","3","4","5","6","7","8","9","10","11","12","13","14","15","16","17","18","19","20","21","22","23","24","25","26","27","28","29","30","31","32","33","34","35","36","37","38","39","40"],["A","A","B","B","C","C","D","D","E","E","F","F","G","G","H","H","I","I","J","J","K","K","L","L","M","M","N","N","O","O","P","P","Q","Q","R","R","S","S","T","T"],["NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES"],[2227,3458,4870,2707,2773,4750,2475,2122,4280,3293,3271,3521,2950,4159,4517,3988,2512,2799,4496,4425,4716,3547,3998,2827,2427,3989,2358,4197,2987,3130,2275,3597,3607,4499,2796,2193,4631,2492,4303,2233],[1134,1576,1510,1279,1224,581,1242,700,1529,624,1584,1471,202,1211,1726,1255,1855,616,1834,1953,987,1441,798,1542,550,1715,1100,1047,1777,1929,543,735,1688,1683,345,1601,1420,1333,1229,958],[1502,1327,1647,1188,1430,1768,806,1875,565,1024,528,1258,603,490,935,438,301,1751,1161,1276,1606,1665,376,783,1143,1560,1571,663,697,1596,726,1128,313,1410,1020,1444,1935,1816,1346,912],[0.39,0.02,0.19,0.29,0.54,0.03,0.04,0.36,0.47,0.38,0.69,0.65,0.46,0.2,0.26,0.77,0.86,0.59,0.22,0.34,0.63,0.83,0.89,0.42,0.94,0.45,0.95,0.58,0.01,0.28,0.32,0.96,0.07,0.76,0.13,0.05,0.85,0.75,0.31,0.23],[-0.02,0.01,0.28,0.12,0.32,0,-0.5,-0.01,0.27,0.24,-0.11,-0.4,-0.06,0.31,0.15,0.41,0.42,-0.05,-0.16,-0.48,0.18,-0.45,0.05,0.02,0.43,0.04,-0.46,-0.25,-0.14,0.37,0.16,-0.34,-0.32,0.44,0.26,-0.43,-0.13,-0.42,-0.09,-0.2]],"container":"<table class=\"display\">\n  <thead>\n    <tr>\n      <th> <\/th>\n      <th>type1<\/th>\n      <th>type2<\/th>\n      <th>value<\/th>\n      <th>value1<\/th>\n      <th>value2<\/th>\n      <th>prob1<\/th>\n      <th>prob2<\/th>\n    <\/tr>\n  <\/thead>\n<\/table>","options":{"pageLength":5,"dom":"ftip","columnDefs":[{"targets":3,"class":"border-left-new"},{"targets":4,"class":"dt-center color"},{"className":"dt-right","targets":[3,4,5,6,7]},{"orderable":false,"targets":0}],"order":[],"autoWidth":false,"orderClasses":false,"lengthMenu":[5,10,25,50,100]}},"evals":[],"jsHooks":[]}</script>

类似地，如果想要自定义样式仅对表头或者表格主体起作用，也需要参照 DataTables 设定地更加详细。比如仅对 th 元素设定样式，引入后就会仅对表头中的单元格起作用，仅对 td 元素设定样式，引入后就会仅对表格主体中的单元格起作用。

## 1.4.通过 formatStyle 函数设置样式

DT 包中封装好的 formatStyle 函数可直接为目标列引入 css 样式。基本语法如下。

``` r
datatable(data) |>
  formatStyle(
    columns, # 指定应用 css 样式的列，具体可填列的序号或列的名称，可填一列或多列
    valueColumns, # 指定获取数据值的列，数据值用于设定不同行的不同 css 属性值
    targets = c("cell", "row"), # 指定应用 css 样式的目标，可以是当前单元格（cell），也可以是行（row）
    color = NULL, # css 样式属性，字体颜色
    backgroud = NULL, # css 样式属性，背景填充
    backgroundColor = NULL, # css 样式属性，背景颜色
    fontWeight = NULL, # css 样式属性，字体粗细
    … # 更多 css 样式属性
  )
```

在 formatStyle 函数中，所有的 css 样式属性的参数值，可以参照 css 语言填写具体属性值，比如定义 `color= 'red'`，那么目标列的字体颜色就会变成红色，也可以引入以下函数，为目标列中不同行设定不同的参数值。

-   `styleInterval(cuts, values)`：参数 cuts 和 values 须填入两个向量，前者表示可将指定列的数值划分成 N 个分段，后者表示为 N 个分段填入 N+1 个不同的 css 样式属性的参数值。
-   `styleEqual(levels, values, default = NULL)`：参数 levels 和 values 须填入两个向量，前者表示可将指定列的数值划分成 N 个等级，后者表示为 N 个等级填入 N 个不同的 css 样式属性的参数值。
-   `styleValue()`：使用指定列中单元格的具体数值作为 css 样式属性的参数值。
-   `styleColorBar(data, color, angle = 90)`：为单元格填充带有颜色的条形图，条形的宽度与单元格中数值大小成正比，其中 angle 参数用于设定旋转角度。
-   `styleRow(rows, values, default = NULL)`：为目标行设定 css 样式属性。

### 1.4.1.单元格背景颜色（backgroundColor）

以下是将多种方法集于一体的复杂例子，为指定的某一列或某几列设置背景颜色，也为不同行设定不同的背景颜色，包括[填充渐变颜色](https://yuanfan.rbind.io/project/dt-fill-color/)。

``` r
#为目标列'value1'准备填充渐变颜色所需的分段向量、颜色向量，当数值由小到大，颜色由白变绿
brks <-
  quantile(data$value1, probs = seq(.05, .95, .05), na.rm = TRUE)
clrs <-
  colorRampPalette(c("#ffffff", "#f2fbd2", "#c9ecb4", "#93d3ab", "#35b0ab"), bias = 2)(length(brks) + 1)

datatable(data) |>
  # 为第1列，即'type1'列设定背景颜色
  formatStyle(columns = 1, backgroundColor = 'green') |>
  # 同时为'prob1'和'prob2'列设定背景颜色
  formatStyle(columns = c('prob1', 'prob2'),
              backgroundColor = 'white') |>
  # 为第2列，即'type2'列中不同的数据设定不同的背景颜色
  formatStyle(columns = 2,
              backgroundColor = styleEqual(
                levels = c('YES', 'NO'),
                values = c('IndianRed', 'Firebrick')
              )) |>
  # 为第3列，即'value'列，按照第2列（'type2'）的数据来设定不同的背景颜色
  formatStyle(
    columns = 3,
    valueColumns = 2,
    backgroundColor = styleEqual(
      levels = c('YES', 'NO'),
      values = c('IndianRed', 'Firebrick')
    )
  ) |>
  # 为第4列，即'value1'列，按照该列的数值设定渐变颜色
  formatStyle(columns = 4,
              backgroundColor = styleInterval(cuts = brks, values = clrs)) |>
  # 目标为每行，按照'prob1'列的数值分段，不同分段的取值范围内设定不同的背景颜色
  # 'prob1'列大于0.5的行为粉色；小于等于0.5且大于0.3为白色；小于等于0.3为灰色
  formatStyle(
    columns = 'prob1',
    target = 'row',
    backgroundColor = styleInterval(
      cuts = c(0.3, 0.5),
      values = c('grey', 'white', 'pink')
    )
  )
```

<div id="htmlwidget-17" style="width:100%;height:auto;" class="datatables html-widget"></div>
<script type="application/json" data-for="htmlwidget-17">{"x":{"filter":"none","vertical":false,"data":[["1","2","3","4","5","6","7","8","9","10","11","12","13","14","15","16","17","18","19","20","21","22","23","24","25","26","27","28","29","30","31","32","33","34","35","36","37","38","39","40"],["A","A","B","B","C","C","D","D","E","E","F","F","G","G","H","H","I","I","J","J","K","K","L","L","M","M","N","N","O","O","P","P","Q","Q","R","R","S","S","T","T"],["NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES"],[2227,3458,4870,2707,2773,4750,2475,2122,4280,3293,3271,3521,2950,4159,4517,3988,2512,2799,4496,4425,4716,3547,3998,2827,2427,3989,2358,4197,2987,3130,2275,3597,3607,4499,2796,2193,4631,2492,4303,2233],[1134,1576,1510,1279,1224,581,1242,700,1529,624,1584,1471,202,1211,1726,1255,1855,616,1834,1953,987,1441,798,1542,550,1715,1100,1047,1777,1929,543,735,1688,1683,345,1601,1420,1333,1229,958],[1502,1327,1647,1188,1430,1768,806,1875,565,1024,528,1258,603,490,935,438,301,1751,1161,1276,1606,1665,376,783,1143,1560,1571,663,697,1596,726,1128,313,1410,1020,1444,1935,1816,1346,912],[0.39,0.02,0.19,0.29,0.54,0.03,0.04,0.36,0.47,0.38,0.69,0.65,0.46,0.2,0.26,0.77,0.86,0.59,0.22,0.34,0.63,0.83,0.89,0.42,0.94,0.45,0.95,0.58,0.01,0.28,0.32,0.96,0.07,0.76,0.13,0.05,0.85,0.75,0.31,0.23],[-0.02,0.01,0.28,0.12,0.32,0,-0.5,-0.01,0.27,0.24,-0.11,-0.4,-0.06,0.31,0.15,0.41,0.42,-0.05,-0.16,-0.48,0.18,-0.45,0.05,0.02,0.43,0.04,-0.46,-0.25,-0.14,0.37,0.16,-0.34,-0.32,0.44,0.26,-0.43,-0.13,-0.42,-0.09,-0.2]],"container":"<table class=\"display\">\n  <thead>\n    <tr>\n      <th> <\/th>\n      <th>type1<\/th>\n      <th>type2<\/th>\n      <th>value<\/th>\n      <th>value1<\/th>\n      <th>value2<\/th>\n      <th>prob1<\/th>\n      <th>prob2<\/th>\n    <\/tr>\n  <\/thead>\n<\/table>","options":{"pageLength":5,"dom":"ftip","columnDefs":[{"className":"dt-right","targets":[3,4,5,6,7]},{"orderable":false,"targets":0}],"order":[],"autoWidth":false,"orderClasses":false,"lengthMenu":[5,10,25,50,100],"rowCallback":"function(row, data, displayNum, displayIndex, dataIndex) {\nvar value=data[1]; $(this.api().cell(row, 1).node()).css({'background-color':'green'});\nvar value=data[6]; $(this.api().cell(row, 6).node()).css({'background-color':'white'});\nvar value=data[7]; $(this.api().cell(row, 7).node()).css({'background-color':'white'});\nvar value=data[2]; $(this.api().cell(row, 2).node()).css({'background-color':value == \"YES\" ? \"IndianRed\" : value == \"NO\" ? \"Firebrick\" : null});\nvar value=data[2]; $(this.api().cell(row, 3).node()).css({'background-color':value == \"YES\" ? \"IndianRed\" : value == \"NO\" ? \"Firebrick\" : null});\nvar value=data[4]; $(this.api().cell(row, 4).node()).css({'background-color':isNaN(parseFloat(value)) ? '' : value <= 533.1 ? \"#FFFFFF\" : value <= 577.9 ? \"#F4FBD9\" : value <= 622.8 ? \"#E8F7CB\" : value <= 728 ? \"#DDF3C2\" : value <= 918 ? \"#D1EFBA\" : value <= 1029 ? \"#C6EAB3\" : value <= 1122.1 ? \"#BDE6B2\" : value <= 1218.8 ? \"#B4E2B0\" : value <= 1236.15 ? \"#ABDEAF\" : value <= 1267 ? \"#A2DAAD\" : value <= 1372.15 ? \"#99D5AC\" : value <= 1453 ? \"#8FD1AB\" : value <= 1516.65 ? \"#84CDAB\" : value <= 1552.2 ? \"#78C9AB\" : value <= 1588.25 ? \"#6DC5AB\" : value <= 1684 ? \"#62C0AB\" : value <= 1716.65 ? \"#56BCAB\" : value <= 1782.7 ? \"#4BB8AB\" : value <= 1858.7 ? \"#40B4AB\" : \"#35B0AB\"});\nvar value=data[6]; $(row).css({'background-color':isNaN(parseFloat(value)) ? '' : value <= 0.3 ? \"grey\" : value <= 0.5 ? \"white\" : \"pink\"});\n}"}},"evals":["options.rowCallback"],"jsHooks":[]}</script>

### 1.4.2.单元格背景填充（background）

在使用 formatStyle 函数时，有两种方法为单元格填充背景。第一种方法，使用 styleColorBar 函数为单元格填充带有颜色的条形，这是 DT 包中专门为单元格背景样式开发的函数，不能挪用到其他样式上去。

``` r
datatable(data) |>
  # 为'value'列填充有颜色的条形图
  formatStyle(
    columns = 'value1',
    background = styleColorBar(data$value1, 'steelblue'),
    # 填充条形
    # 填充背景的尺寸，第一个值为宽度，第二个值为高度
    backgroundSize = '100% 90%',
    backgroundRepeat = 'no-repeat',
    backgroundPosition = 'center',
    textAlign = 'left'
  ) |>
  # 为'value1'列填充有颜色的条形图
  formatStyle(
    columns = 'value2',
    background = styleColorBar(data$value2, color = '#00bfff'),
    backgroundSize = '90% 50%',
    backgroundRepeat = 'no-repeat',
    backgroundPosition = 'center',
    color = 'white'
  )
```

<div id="htmlwidget-18" style="width:100%;height:auto;" class="datatables html-widget"></div>
<script type="application/json" data-for="htmlwidget-18">{"x":{"filter":"none","vertical":false,"data":[["1","2","3","4","5","6","7","8","9","10","11","12","13","14","15","16","17","18","19","20","21","22","23","24","25","26","27","28","29","30","31","32","33","34","35","36","37","38","39","40"],["A","A","B","B","C","C","D","D","E","E","F","F","G","G","H","H","I","I","J","J","K","K","L","L","M","M","N","N","O","O","P","P","Q","Q","R","R","S","S","T","T"],["NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES"],[2227,3458,4870,2707,2773,4750,2475,2122,4280,3293,3271,3521,2950,4159,4517,3988,2512,2799,4496,4425,4716,3547,3998,2827,2427,3989,2358,4197,2987,3130,2275,3597,3607,4499,2796,2193,4631,2492,4303,2233],[1134,1576,1510,1279,1224,581,1242,700,1529,624,1584,1471,202,1211,1726,1255,1855,616,1834,1953,987,1441,798,1542,550,1715,1100,1047,1777,1929,543,735,1688,1683,345,1601,1420,1333,1229,958],[1502,1327,1647,1188,1430,1768,806,1875,565,1024,528,1258,603,490,935,438,301,1751,1161,1276,1606,1665,376,783,1143,1560,1571,663,697,1596,726,1128,313,1410,1020,1444,1935,1816,1346,912],[0.39,0.02,0.19,0.29,0.54,0.03,0.04,0.36,0.47,0.38,0.69,0.65,0.46,0.2,0.26,0.77,0.86,0.59,0.22,0.34,0.63,0.83,0.89,0.42,0.94,0.45,0.95,0.58,0.01,0.28,0.32,0.96,0.07,0.76,0.13,0.05,0.85,0.75,0.31,0.23],[-0.02,0.01,0.28,0.12,0.32,0,-0.5,-0.01,0.27,0.24,-0.11,-0.4,-0.06,0.31,0.15,0.41,0.42,-0.05,-0.16,-0.48,0.18,-0.45,0.05,0.02,0.43,0.04,-0.46,-0.25,-0.14,0.37,0.16,-0.34,-0.32,0.44,0.26,-0.43,-0.13,-0.42,-0.09,-0.2]],"container":"<table class=\"display\">\n  <thead>\n    <tr>\n      <th> <\/th>\n      <th>type1<\/th>\n      <th>type2<\/th>\n      <th>value<\/th>\n      <th>value1<\/th>\n      <th>value2<\/th>\n      <th>prob1<\/th>\n      <th>prob2<\/th>\n    <\/tr>\n  <\/thead>\n<\/table>","options":{"pageLength":5,"dom":"ftip","columnDefs":[{"className":"dt-right","targets":[3,4,5,6,7]},{"orderable":false,"targets":0}],"order":[],"autoWidth":false,"orderClasses":false,"lengthMenu":[5,10,25,50,100],"rowCallback":"function(row, data, displayNum, displayIndex, dataIndex) {\nvar value=data[4]; $(this.api().cell(row, 4).node()).css({'background':isNaN(parseFloat(value)) || value <= 202.000000 ? '' : 'linear-gradient(90.000000deg, transparent ' + Math.max(1953.000000 - value, 0)/1751.000000 * 100 + '%, steelblue ' + Math.max(1953.000000 - value, 0)/1751.000000 * 100 + '%)','background-size':'100% 90%','background-repeat':'no-repeat','background-position':'center','text-align':'left'});\nvar value=data[5]; $(this.api().cell(row, 5).node()).css({'color':'white','background':isNaN(parseFloat(value)) || value <= 301.000000 ? '' : 'linear-gradient(90.000000deg, transparent ' + Math.max(1935.000000 - value, 0)/1634.000000 * 100 + '%, #00bfff ' + Math.max(1935.000000 - value, 0)/1634.000000 * 100 + '%)','background-size':'90% 50%','background-repeat':'no-repeat','background-position':'center'});\n}"}},"evals":["options.rowCallback"],"jsHooks":[]}</script>

第二种方法是直接写入具体的 css 样式属性来填充背景形状。需要说明的是，在 formatStyle 函数中填入的 css 样式属性有两种写法：一是照搬 css，但需要为填入的各 css 样式属性加上引号，比如`'font-weight'`、`'font-size'`、`background-color`；二是如前述小节一样，各 css 样式属性中`-`后面的首字母改成大写。

``` r
# 准备渐变色
brks <-
  quantile(data$value, probs = seq(.05, .95, .05), na.rm = TRUE)
# 渐变色由红变绿，bias>1，则绿色更多；bias<1，则红色更多
clrs <-
  colorRampPalette(c("#ff2700", "#f8fcf8", "#44ab43"), bias = 1.3)(length(brks) + 1)

datatable(data)|>
  formatStyle(
    columns = 'value',
    'background-color' = styleInterval(cuts = brks, values = clrs),
    'display' = 'flex',
    'margin' = 'auto',
    'align-items' = 'center',
    'justify-content' = 'center',
    'width' = '1.875rem',
    'height' = '1.875rem',
    'border' = '0.5px solid rgb(0,0,0,0.1)',
    'border-radius' = '50%',
    'color' = '#000',
    'font-size' = '0.8125rem',
    'letter-spacing' = '-1px'
  ) 
```

<div id="htmlwidget-19" style="width:100%;height:auto;" class="datatables html-widget"></div>
<script type="application/json" data-for="htmlwidget-19">{"x":{"filter":"none","vertical":false,"data":[["1","2","3","4","5","6","7","8","9","10","11","12","13","14","15","16","17","18","19","20","21","22","23","24","25","26","27","28","29","30","31","32","33","34","35","36","37","38","39","40"],["A","A","B","B","C","C","D","D","E","E","F","F","G","G","H","H","I","I","J","J","K","K","L","L","M","M","N","N","O","O","P","P","Q","Q","R","R","S","S","T","T"],["NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES"],[2227,3458,4870,2707,2773,4750,2475,2122,4280,3293,3271,3521,2950,4159,4517,3988,2512,2799,4496,4425,4716,3547,3998,2827,2427,3989,2358,4197,2987,3130,2275,3597,3607,4499,2796,2193,4631,2492,4303,2233],[1134,1576,1510,1279,1224,581,1242,700,1529,624,1584,1471,202,1211,1726,1255,1855,616,1834,1953,987,1441,798,1542,550,1715,1100,1047,1777,1929,543,735,1688,1683,345,1601,1420,1333,1229,958],[1502,1327,1647,1188,1430,1768,806,1875,565,1024,528,1258,603,490,935,438,301,1751,1161,1276,1606,1665,376,783,1143,1560,1571,663,697,1596,726,1128,313,1410,1020,1444,1935,1816,1346,912],[0.39,0.02,0.19,0.29,0.54,0.03,0.04,0.36,0.47,0.38,0.69,0.65,0.46,0.2,0.26,0.77,0.86,0.59,0.22,0.34,0.63,0.83,0.89,0.42,0.94,0.45,0.95,0.58,0.01,0.28,0.32,0.96,0.07,0.76,0.13,0.05,0.85,0.75,0.31,0.23],[-0.02,0.01,0.28,0.12,0.32,0,-0.5,-0.01,0.27,0.24,-0.11,-0.4,-0.06,0.31,0.15,0.41,0.42,-0.05,-0.16,-0.48,0.18,-0.45,0.05,0.02,0.43,0.04,-0.46,-0.25,-0.14,0.37,0.16,-0.34,-0.32,0.44,0.26,-0.43,-0.13,-0.42,-0.09,-0.2]],"container":"<table class=\"display\">\n  <thead>\n    <tr>\n      <th> <\/th>\n      <th>type1<\/th>\n      <th>type2<\/th>\n      <th>value<\/th>\n      <th>value1<\/th>\n      <th>value2<\/th>\n      <th>prob1<\/th>\n      <th>prob2<\/th>\n    <\/tr>\n  <\/thead>\n<\/table>","options":{"pageLength":5,"dom":"ftip","columnDefs":[{"className":"dt-right","targets":[3,4,5,6,7]},{"orderable":false,"targets":0}],"order":[],"autoWidth":false,"orderClasses":false,"lengthMenu":[5,10,25,50,100],"rowCallback":"function(row, data, displayNum, displayIndex, dataIndex) {\nvar value=data[3]; $(this.api().cell(row, 3).node()).css({'color':'#000','background-color':isNaN(parseFloat(value)) ? '' : value <= 2225.3 ? \"#FF2700\" : value <= 2270.8 ? \"#FE4220\" : value <= 2416.65 ? \"#FD5E40\" : value <= 2488.6 ? \"#FC7960\" : value <= 2658.25 ? \"#FB9580\" : value <= 2789.1 ? \"#FAB1A0\" : value <= 2817.2 ? \"#F9CCC0\" : value <= 2972.2 ? \"#F8E8E0\" : value <= 3207.55 ? \"#F3F9F3\" : value <= 3375.5 ? \"#E3F2E3\" : value <= 3532.7 ? \"#D3EBD3\" : value <= 3601 ? \"#C3E4C3\" : value <= 3988.35 ? \"#B3DDB3\" : value <= 4046.3 ? \"#A3D6A3\" : value <= 4217.75 ? \"#93CE93\" : value <= 4327.4 ? \"#83C783\" : value <= 4496.45 ? \"#73C073\" : value <= 4528.4 ? \"#63B963\" : value <= 4717.7 ? \"#53B253\" : \"#44AB43\",'display':'flex','margin':'auto','align-items':'center','justify-content':'center','width':'1.875rem','height':'1.875rem','border':'0.5px solid rgb(0,0,0,0.1)','border-radius':'50%','font-size':'0.8125rem','letter-spacing':'-1px'});\n}"}},"evals":["options.rowCallback"],"jsHooks":[]}</script>

### 1.4.3.字体（font）

可以给目标列设置各种不同的 css 字体样式，如字体粗细、字体颜色、字体大小等。

-   字体粗细（fontWeight）

``` r
datatable(data) |>
  # 为第1列，即'type1'列设定字体粗细为加粗
  formatStyle(columns = 1, fontWeight = 'bold') |>
  # 目标为行，按照第2列（'type2'列）的数据值，设定每隔一行字体加粗
  formatStyle(
    columns = 2,
    target = 'row',
    fontWeight = styleRow(rows = seq(
      from = 1,
      to = nrow(data),
      by = 2
    ), values = 'bold')
  )
```

<div id="htmlwidget-20" style="width:100%;height:auto;" class="datatables html-widget"></div>
<script type="application/json" data-for="htmlwidget-20">{"x":{"filter":"none","vertical":false,"data":[["1","2","3","4","5","6","7","8","9","10","11","12","13","14","15","16","17","18","19","20","21","22","23","24","25","26","27","28","29","30","31","32","33","34","35","36","37","38","39","40"],["A","A","B","B","C","C","D","D","E","E","F","F","G","G","H","H","I","I","J","J","K","K","L","L","M","M","N","N","O","O","P","P","Q","Q","R","R","S","S","T","T"],["NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES"],[2227,3458,4870,2707,2773,4750,2475,2122,4280,3293,3271,3521,2950,4159,4517,3988,2512,2799,4496,4425,4716,3547,3998,2827,2427,3989,2358,4197,2987,3130,2275,3597,3607,4499,2796,2193,4631,2492,4303,2233],[1134,1576,1510,1279,1224,581,1242,700,1529,624,1584,1471,202,1211,1726,1255,1855,616,1834,1953,987,1441,798,1542,550,1715,1100,1047,1777,1929,543,735,1688,1683,345,1601,1420,1333,1229,958],[1502,1327,1647,1188,1430,1768,806,1875,565,1024,528,1258,603,490,935,438,301,1751,1161,1276,1606,1665,376,783,1143,1560,1571,663,697,1596,726,1128,313,1410,1020,1444,1935,1816,1346,912],[0.39,0.02,0.19,0.29,0.54,0.03,0.04,0.36,0.47,0.38,0.69,0.65,0.46,0.2,0.26,0.77,0.86,0.59,0.22,0.34,0.63,0.83,0.89,0.42,0.94,0.45,0.95,0.58,0.01,0.28,0.32,0.96,0.07,0.76,0.13,0.05,0.85,0.75,0.31,0.23],[-0.02,0.01,0.28,0.12,0.32,0,-0.5,-0.01,0.27,0.24,-0.11,-0.4,-0.06,0.31,0.15,0.41,0.42,-0.05,-0.16,-0.48,0.18,-0.45,0.05,0.02,0.43,0.04,-0.46,-0.25,-0.14,0.37,0.16,-0.34,-0.32,0.44,0.26,-0.43,-0.13,-0.42,-0.09,-0.2]],"container":"<table class=\"display\">\n  <thead>\n    <tr>\n      <th> <\/th>\n      <th>type1<\/th>\n      <th>type2<\/th>\n      <th>value<\/th>\n      <th>value1<\/th>\n      <th>value2<\/th>\n      <th>prob1<\/th>\n      <th>prob2<\/th>\n    <\/tr>\n  <\/thead>\n<\/table>","options":{"pageLength":5,"dom":"ftip","columnDefs":[{"className":"dt-right","targets":[3,4,5,6,7]},{"orderable":false,"targets":0}],"order":[],"autoWidth":false,"orderClasses":false,"lengthMenu":[5,10,25,50,100],"rowCallback":"function(row, data, displayNum, displayIndex, dataIndex) {\nvar value=data[1]; $(this.api().cell(row, 1).node()).css({'font-weight':'bold'});\nvar value=data[2]; $(row).css({'font-weight':$.inArray(dataIndex + 1, [1]) >= 0 ? \"bold\" : $.inArray(dataIndex + 1, [3]) >= 0 ? \"bold\" : $.inArray(dataIndex + 1, [5]) >= 0 ? \"bold\" : $.inArray(dataIndex + 1, [7]) >= 0 ? \"bold\" : $.inArray(dataIndex + 1, [9]) >= 0 ? \"bold\" : $.inArray(dataIndex + 1, [11]) >= 0 ? \"bold\" : $.inArray(dataIndex + 1, [13]) >= 0 ? \"bold\" : $.inArray(dataIndex + 1, [15]) >= 0 ? \"bold\" : $.inArray(dataIndex + 1, [17]) >= 0 ? \"bold\" : $.inArray(dataIndex + 1, [19]) >= 0 ? \"bold\" : $.inArray(dataIndex + 1, [21]) >= 0 ? \"bold\" : $.inArray(dataIndex + 1, [23]) >= 0 ? \"bold\" : $.inArray(dataIndex + 1, [25]) >= 0 ? \"bold\" : $.inArray(dataIndex + 1, [27]) >= 0 ? \"bold\" : $.inArray(dataIndex + 1, [29]) >= 0 ? \"bold\" : $.inArray(dataIndex + 1, [31]) >= 0 ? \"bold\" : $.inArray(dataIndex + 1, [33]) >= 0 ? \"bold\" : $.inArray(dataIndex + 1, [35]) >= 0 ? \"bold\" : $.inArray(dataIndex + 1, [37]) >= 0 ? \"bold\" : $.inArray(dataIndex + 1, [39]) >= 0 ? \"bold\" : null});\n}"}},"evals":["options.rowCallback"],"jsHooks":[]}</script>

-   字体颜色（color）

``` r
datatable(data) |>
  # 为第1列，即'type1'列设定字体粗细为加粗
  formatStyle(columns = 1, color = 'red') |>
  # 目标为行，按照第2列（'type2'列）的数据值，设定不同行应用不同的字体颜色
  formatStyle(
    columns = 2,
    target = 'row',
    color = styleEqual(
      levels = c('YES', 'NO'),
      values = c('green', 'red')
    )
  )
```

<div id="htmlwidget-21" style="width:100%;height:auto;" class="datatables html-widget"></div>
<script type="application/json" data-for="htmlwidget-21">{"x":{"filter":"none","vertical":false,"data":[["1","2","3","4","5","6","7","8","9","10","11","12","13","14","15","16","17","18","19","20","21","22","23","24","25","26","27","28","29","30","31","32","33","34","35","36","37","38","39","40"],["A","A","B","B","C","C","D","D","E","E","F","F","G","G","H","H","I","I","J","J","K","K","L","L","M","M","N","N","O","O","P","P","Q","Q","R","R","S","S","T","T"],["NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES"],[2227,3458,4870,2707,2773,4750,2475,2122,4280,3293,3271,3521,2950,4159,4517,3988,2512,2799,4496,4425,4716,3547,3998,2827,2427,3989,2358,4197,2987,3130,2275,3597,3607,4499,2796,2193,4631,2492,4303,2233],[1134,1576,1510,1279,1224,581,1242,700,1529,624,1584,1471,202,1211,1726,1255,1855,616,1834,1953,987,1441,798,1542,550,1715,1100,1047,1777,1929,543,735,1688,1683,345,1601,1420,1333,1229,958],[1502,1327,1647,1188,1430,1768,806,1875,565,1024,528,1258,603,490,935,438,301,1751,1161,1276,1606,1665,376,783,1143,1560,1571,663,697,1596,726,1128,313,1410,1020,1444,1935,1816,1346,912],[0.39,0.02,0.19,0.29,0.54,0.03,0.04,0.36,0.47,0.38,0.69,0.65,0.46,0.2,0.26,0.77,0.86,0.59,0.22,0.34,0.63,0.83,0.89,0.42,0.94,0.45,0.95,0.58,0.01,0.28,0.32,0.96,0.07,0.76,0.13,0.05,0.85,0.75,0.31,0.23],[-0.02,0.01,0.28,0.12,0.32,0,-0.5,-0.01,0.27,0.24,-0.11,-0.4,-0.06,0.31,0.15,0.41,0.42,-0.05,-0.16,-0.48,0.18,-0.45,0.05,0.02,0.43,0.04,-0.46,-0.25,-0.14,0.37,0.16,-0.34,-0.32,0.44,0.26,-0.43,-0.13,-0.42,-0.09,-0.2]],"container":"<table class=\"display\">\n  <thead>\n    <tr>\n      <th> <\/th>\n      <th>type1<\/th>\n      <th>type2<\/th>\n      <th>value<\/th>\n      <th>value1<\/th>\n      <th>value2<\/th>\n      <th>prob1<\/th>\n      <th>prob2<\/th>\n    <\/tr>\n  <\/thead>\n<\/table>","options":{"pageLength":5,"dom":"ftip","columnDefs":[{"className":"dt-right","targets":[3,4,5,6,7]},{"orderable":false,"targets":0}],"order":[],"autoWidth":false,"orderClasses":false,"lengthMenu":[5,10,25,50,100],"rowCallback":"function(row, data, displayNum, displayIndex, dataIndex) {\nvar value=data[1]; $(this.api().cell(row, 1).node()).css({'color':'red'});\nvar value=data[2]; $(row).css({'color':value == \"YES\" ? \"green\" : value == \"NO\" ? \"red\" : null});\n}"}},"evals":["options.rowCallback"],"jsHooks":[]}</script>

-   字体大小（fontSize）

``` r
datatable(data) |>
  # 为第1列，即'type1'列设定字体大小
  formatStyle(columns = 1, fontSize = '18px') |>
  # 目标为行，按照'prob1'列的数据值，设定不同行应用不同的字体大小
  formatStyle(
    columns = 'prob1',
    target = 'row',
    fontSize = styleInterval(
      cuts = c(0.3, 0.5),
      values = c('18px', '14px', '10px')
    )
  )
```

<div id="htmlwidget-22" style="width:100%;height:auto;" class="datatables html-widget"></div>
<script type="application/json" data-for="htmlwidget-22">{"x":{"filter":"none","vertical":false,"data":[["1","2","3","4","5","6","7","8","9","10","11","12","13","14","15","16","17","18","19","20","21","22","23","24","25","26","27","28","29","30","31","32","33","34","35","36","37","38","39","40"],["A","A","B","B","C","C","D","D","E","E","F","F","G","G","H","H","I","I","J","J","K","K","L","L","M","M","N","N","O","O","P","P","Q","Q","R","R","S","S","T","T"],["NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES"],[2227,3458,4870,2707,2773,4750,2475,2122,4280,3293,3271,3521,2950,4159,4517,3988,2512,2799,4496,4425,4716,3547,3998,2827,2427,3989,2358,4197,2987,3130,2275,3597,3607,4499,2796,2193,4631,2492,4303,2233],[1134,1576,1510,1279,1224,581,1242,700,1529,624,1584,1471,202,1211,1726,1255,1855,616,1834,1953,987,1441,798,1542,550,1715,1100,1047,1777,1929,543,735,1688,1683,345,1601,1420,1333,1229,958],[1502,1327,1647,1188,1430,1768,806,1875,565,1024,528,1258,603,490,935,438,301,1751,1161,1276,1606,1665,376,783,1143,1560,1571,663,697,1596,726,1128,313,1410,1020,1444,1935,1816,1346,912],[0.39,0.02,0.19,0.29,0.54,0.03,0.04,0.36,0.47,0.38,0.69,0.65,0.46,0.2,0.26,0.77,0.86,0.59,0.22,0.34,0.63,0.83,0.89,0.42,0.94,0.45,0.95,0.58,0.01,0.28,0.32,0.96,0.07,0.76,0.13,0.05,0.85,0.75,0.31,0.23],[-0.02,0.01,0.28,0.12,0.32,0,-0.5,-0.01,0.27,0.24,-0.11,-0.4,-0.06,0.31,0.15,0.41,0.42,-0.05,-0.16,-0.48,0.18,-0.45,0.05,0.02,0.43,0.04,-0.46,-0.25,-0.14,0.37,0.16,-0.34,-0.32,0.44,0.26,-0.43,-0.13,-0.42,-0.09,-0.2]],"container":"<table class=\"display\">\n  <thead>\n    <tr>\n      <th> <\/th>\n      <th>type1<\/th>\n      <th>type2<\/th>\n      <th>value<\/th>\n      <th>value1<\/th>\n      <th>value2<\/th>\n      <th>prob1<\/th>\n      <th>prob2<\/th>\n    <\/tr>\n  <\/thead>\n<\/table>","options":{"pageLength":5,"dom":"ftip","columnDefs":[{"className":"dt-right","targets":[3,4,5,6,7]},{"orderable":false,"targets":0}],"order":[],"autoWidth":false,"orderClasses":false,"lengthMenu":[5,10,25,50,100],"rowCallback":"function(row, data, displayNum, displayIndex, dataIndex) {\nvar value=data[1]; $(this.api().cell(row, 1).node()).css({'font-size':'18px'});\nvar value=data[6]; $(row).css({'font-size':isNaN(parseFloat(value)) ? '' : value <= 0.3 ? \"18px\" : value <= 0.5 ? \"14px\" : \"10px\"});\n}"}},"evals":["options.rowCallback"],"jsHooks":[]}</script>

### 1.4.4.边框（border）

css 的[边框](https://www.w3school.com.cn/cssref/pr_border.asp)包含三种具体样式，即边框的宽度、边框的线型、边框的颜色，且单元格的上下左右四条边框均可单独设置。

-   ‘border’：此参数中可依次填入三种参数值

    -   border-width，边框的宽度
    -   border-style，边框的线型，如实线solid，虚线dashed，点线dotted
    -   border-color，边框的颜色

-   ‘border-bottom’：下边框

-   ‘border-top’：上边框

-   ‘border-left’：左边框

-   ‘border-right’：右边框

``` r
datatable(data) |>
  # 为第1列，即'type1'列，设定单元格的边框样式为宽度1px、虚线、黑色
  formatStyle(columns = 1, 'border' = '1px dashed black') |>
  # 为第3列，即'value'列，设定单元格的下边框样式为宽度1px、实线、黑色
  formatStyle(columns = 3, 'border-bottom' = '1px solid black') |>
  # 为第4列，即'value1'列，设定单元格的上边框样式为宽度1px、点线、黑色
  formatStyle(columns = 4, 'border-top' = '1px dotted black') |>
  # 为第5列，即'value2'列，设定单元格的左边框样式为宽度2px、实线、红色
  formatStyle(columns = 5, 'border-left' = '2px solid red') |>
  # 为第6/7列，即'prob1'和'prob2'列，设定单元格的右边框为宽度1px、实线、黑色
  formatStyle(columns = c(6, 7), 'border-right' = '1px solid black')
```

<div id="htmlwidget-23" style="width:100%;height:auto;" class="datatables html-widget"></div>
<script type="application/json" data-for="htmlwidget-23">{"x":{"filter":"none","vertical":false,"data":[["1","2","3","4","5","6","7","8","9","10","11","12","13","14","15","16","17","18","19","20","21","22","23","24","25","26","27","28","29","30","31","32","33","34","35","36","37","38","39","40"],["A","A","B","B","C","C","D","D","E","E","F","F","G","G","H","H","I","I","J","J","K","K","L","L","M","M","N","N","O","O","P","P","Q","Q","R","R","S","S","T","T"],["NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES"],[2227,3458,4870,2707,2773,4750,2475,2122,4280,3293,3271,3521,2950,4159,4517,3988,2512,2799,4496,4425,4716,3547,3998,2827,2427,3989,2358,4197,2987,3130,2275,3597,3607,4499,2796,2193,4631,2492,4303,2233],[1134,1576,1510,1279,1224,581,1242,700,1529,624,1584,1471,202,1211,1726,1255,1855,616,1834,1953,987,1441,798,1542,550,1715,1100,1047,1777,1929,543,735,1688,1683,345,1601,1420,1333,1229,958],[1502,1327,1647,1188,1430,1768,806,1875,565,1024,528,1258,603,490,935,438,301,1751,1161,1276,1606,1665,376,783,1143,1560,1571,663,697,1596,726,1128,313,1410,1020,1444,1935,1816,1346,912],[0.39,0.02,0.19,0.29,0.54,0.03,0.04,0.36,0.47,0.38,0.69,0.65,0.46,0.2,0.26,0.77,0.86,0.59,0.22,0.34,0.63,0.83,0.89,0.42,0.94,0.45,0.95,0.58,0.01,0.28,0.32,0.96,0.07,0.76,0.13,0.05,0.85,0.75,0.31,0.23],[-0.02,0.01,0.28,0.12,0.32,0,-0.5,-0.01,0.27,0.24,-0.11,-0.4,-0.06,0.31,0.15,0.41,0.42,-0.05,-0.16,-0.48,0.18,-0.45,0.05,0.02,0.43,0.04,-0.46,-0.25,-0.14,0.37,0.16,-0.34,-0.32,0.44,0.26,-0.43,-0.13,-0.42,-0.09,-0.2]],"container":"<table class=\"display\">\n  <thead>\n    <tr>\n      <th> <\/th>\n      <th>type1<\/th>\n      <th>type2<\/th>\n      <th>value<\/th>\n      <th>value1<\/th>\n      <th>value2<\/th>\n      <th>prob1<\/th>\n      <th>prob2<\/th>\n    <\/tr>\n  <\/thead>\n<\/table>","options":{"pageLength":5,"dom":"ftip","columnDefs":[{"className":"dt-right","targets":[3,4,5,6,7]},{"orderable":false,"targets":0}],"order":[],"autoWidth":false,"orderClasses":false,"lengthMenu":[5,10,25,50,100],"rowCallback":"function(row, data, displayNum, displayIndex, dataIndex) {\nvar value=data[1]; $(this.api().cell(row, 1).node()).css({'border':'1px dashed black'});\nvar value=data[3]; $(this.api().cell(row, 3).node()).css({'border-bottom':'1px solid black'});\nvar value=data[4]; $(this.api().cell(row, 4).node()).css({'border-top':'1px dotted black'});\nvar value=data[5]; $(this.api().cell(row, 5).node()).css({'border-left':'2px solid red'});\nvar value=data[6]; $(this.api().cell(row, 6).node()).css({'border-right':'1px solid black'});\nvar value=data[7]; $(this.api().cell(row, 7).node()).css({'border-right':'1px solid black'});\n}"}},"evals":["options.rowCallback"],"jsHooks":[]}</script>

### 1.4.5.文本对齐（textAlign）

为单元格设置文本对齐方式时，有两点需要注意。

-   其一，一般情况下，由于 formatStyle 函数中设定的各类 css 样式属性仅仅会对表格主体起作用，不会对表头起作用，因此若想要同时修改表头的样式，可参考1.3.3小节中的方法来设定仅对表头起作用的样式，或直接引用默认样式。

-   其二，在 formatStyle 函数中设定 `target = 'row'` 时，会改变表格中整行的样式，若不希望其他列受影响，还需要单独设定。

``` r
datatable(data, options = list(columnDefs = list(
  list(targets = '_all', className = 'dt-head-center')
))) |>
  # 为第1、3-7列设定文本对齐方式为居中
  formatStyle(columns = c(1, 3:7), textAlign = 'center') |>
  # 目标为行，按照第2列（'type2'列）的数据值，设定不同行应用不同的文本对齐方式
  formatStyle(
    columns = 2,
    target = 'row',
    textAlign = styleEqual(
      levels = c('YES', 'NO'),
      values = c('left', 'right')
    )
  )
```

<div id="htmlwidget-24" style="width:100%;height:auto;" class="datatables html-widget"></div>
<script type="application/json" data-for="htmlwidget-24">{"x":{"filter":"none","vertical":false,"data":[["1","2","3","4","5","6","7","8","9","10","11","12","13","14","15","16","17","18","19","20","21","22","23","24","25","26","27","28","29","30","31","32","33","34","35","36","37","38","39","40"],["A","A","B","B","C","C","D","D","E","E","F","F","G","G","H","H","I","I","J","J","K","K","L","L","M","M","N","N","O","O","P","P","Q","Q","R","R","S","S","T","T"],["NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES"],[2227,3458,4870,2707,2773,4750,2475,2122,4280,3293,3271,3521,2950,4159,4517,3988,2512,2799,4496,4425,4716,3547,3998,2827,2427,3989,2358,4197,2987,3130,2275,3597,3607,4499,2796,2193,4631,2492,4303,2233],[1134,1576,1510,1279,1224,581,1242,700,1529,624,1584,1471,202,1211,1726,1255,1855,616,1834,1953,987,1441,798,1542,550,1715,1100,1047,1777,1929,543,735,1688,1683,345,1601,1420,1333,1229,958],[1502,1327,1647,1188,1430,1768,806,1875,565,1024,528,1258,603,490,935,438,301,1751,1161,1276,1606,1665,376,783,1143,1560,1571,663,697,1596,726,1128,313,1410,1020,1444,1935,1816,1346,912],[0.39,0.02,0.19,0.29,0.54,0.03,0.04,0.36,0.47,0.38,0.69,0.65,0.46,0.2,0.26,0.77,0.86,0.59,0.22,0.34,0.63,0.83,0.89,0.42,0.94,0.45,0.95,0.58,0.01,0.28,0.32,0.96,0.07,0.76,0.13,0.05,0.85,0.75,0.31,0.23],[-0.02,0.01,0.28,0.12,0.32,0,-0.5,-0.01,0.27,0.24,-0.11,-0.4,-0.06,0.31,0.15,0.41,0.42,-0.05,-0.16,-0.48,0.18,-0.45,0.05,0.02,0.43,0.04,-0.46,-0.25,-0.14,0.37,0.16,-0.34,-0.32,0.44,0.26,-0.43,-0.13,-0.42,-0.09,-0.2]],"container":"<table class=\"display\">\n  <thead>\n    <tr>\n      <th> <\/th>\n      <th>type1<\/th>\n      <th>type2<\/th>\n      <th>value<\/th>\n      <th>value1<\/th>\n      <th>value2<\/th>\n      <th>prob1<\/th>\n      <th>prob2<\/th>\n    <\/tr>\n  <\/thead>\n<\/table>","options":{"pageLength":5,"dom":"ftip","columnDefs":[{"targets":"_all","className":"dt-head-center"},{"orderable":false,"targets":0}],"order":[],"autoWidth":false,"orderClasses":false,"lengthMenu":[5,10,25,50,100],"rowCallback":"function(row, data, displayNum, displayIndex, dataIndex) {\nvar value=data[1]; $(this.api().cell(row, 1).node()).css({'text-align':'center'});\nvar value=data[3]; $(this.api().cell(row, 3).node()).css({'text-align':'center'});\nvar value=data[4]; $(this.api().cell(row, 4).node()).css({'text-align':'center'});\nvar value=data[5]; $(this.api().cell(row, 5).node()).css({'text-align':'center'});\nvar value=data[6]; $(this.api().cell(row, 6).node()).css({'text-align':'center'});\nvar value=data[7]; $(this.api().cell(row, 7).node()).css({'text-align':'center'});\nvar value=data[2]; $(row).css({'text-align':value == \"YES\" ? \"left\" : value == \"NO\" ? \"right\" : null});\n}"}},"evals":["options.rowCallback"],"jsHooks":[]}</script>

## 1.5.引入 JS 设置样式

本小节仅介绍通过引入 JS 来引入 html 元素，在此基础上设定 css 样式，从而达到设置表格样式的目的。

### 1.5.1.调用 DataTables API 设置样式

DataTables 中的 [API](https://datatables.net/reference/api/) 功能非常丰富，本小节只简单介绍用于设置表格样式的方法，不多深究。具体方法是使用 DT 包中的初始化回调函数 `initComplete = JS()` 来调用 DataTables API，再引入 css 来设置各个表格元素的样式，以下是几个简单例子。

-   表格表头，`table().header()`。

``` r
datatable(data,
          options = list(
            initComplete = JS(
              "function(settings, json) {
    $(this.api().table().header()).css({'background-color': 'black', 'color': 'green','font-size':'18px'});
    }")))
```

<div id="htmlwidget-25" style="width:100%;height:auto;" class="datatables html-widget"></div>
<script type="application/json" data-for="htmlwidget-25">{"x":{"filter":"none","vertical":false,"data":[["1","2","3","4","5","6","7","8","9","10","11","12","13","14","15","16","17","18","19","20","21","22","23","24","25","26","27","28","29","30","31","32","33","34","35","36","37","38","39","40"],["A","A","B","B","C","C","D","D","E","E","F","F","G","G","H","H","I","I","J","J","K","K","L","L","M","M","N","N","O","O","P","P","Q","Q","R","R","S","S","T","T"],["NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES"],[2227,3458,4870,2707,2773,4750,2475,2122,4280,3293,3271,3521,2950,4159,4517,3988,2512,2799,4496,4425,4716,3547,3998,2827,2427,3989,2358,4197,2987,3130,2275,3597,3607,4499,2796,2193,4631,2492,4303,2233],[1134,1576,1510,1279,1224,581,1242,700,1529,624,1584,1471,202,1211,1726,1255,1855,616,1834,1953,987,1441,798,1542,550,1715,1100,1047,1777,1929,543,735,1688,1683,345,1601,1420,1333,1229,958],[1502,1327,1647,1188,1430,1768,806,1875,565,1024,528,1258,603,490,935,438,301,1751,1161,1276,1606,1665,376,783,1143,1560,1571,663,697,1596,726,1128,313,1410,1020,1444,1935,1816,1346,912],[0.39,0.02,0.19,0.29,0.54,0.03,0.04,0.36,0.47,0.38,0.69,0.65,0.46,0.2,0.26,0.77,0.86,0.59,0.22,0.34,0.63,0.83,0.89,0.42,0.94,0.45,0.95,0.58,0.01,0.28,0.32,0.96,0.07,0.76,0.13,0.05,0.85,0.75,0.31,0.23],[-0.02,0.01,0.28,0.12,0.32,0,-0.5,-0.01,0.27,0.24,-0.11,-0.4,-0.06,0.31,0.15,0.41,0.42,-0.05,-0.16,-0.48,0.18,-0.45,0.05,0.02,0.43,0.04,-0.46,-0.25,-0.14,0.37,0.16,-0.34,-0.32,0.44,0.26,-0.43,-0.13,-0.42,-0.09,-0.2]],"container":"<table class=\"display\">\n  <thead>\n    <tr>\n      <th> <\/th>\n      <th>type1<\/th>\n      <th>type2<\/th>\n      <th>value<\/th>\n      <th>value1<\/th>\n      <th>value2<\/th>\n      <th>prob1<\/th>\n      <th>prob2<\/th>\n    <\/tr>\n  <\/thead>\n<\/table>","options":{"pageLength":5,"dom":"ftip","initComplete":"function(settings, json) {\n    $(this.api().table().header()).css({'background-color': 'black', 'color': 'green','font-size':'18px'});\n    }","columnDefs":[{"className":"dt-right","targets":[3,4,5,6,7]},{"orderable":false,"targets":0}],"order":[],"autoWidth":false,"orderClasses":false,"lengthMenu":[5,10,25,50,100]}},"evals":["options.initComplete"],"jsHooks":[]}</script>

-   表格主体，`tables().body()`。

``` r
datatable(data, options = list(
  initComplete = JS(
    "function(settings, json) {
    $(this.api().tables().body()).css({'color': 'red', 'font-size':'14px'});
    }")
))
```

<div id="htmlwidget-26" style="width:100%;height:auto;" class="datatables html-widget"></div>
<script type="application/json" data-for="htmlwidget-26">{"x":{"filter":"none","vertical":false,"data":[["1","2","3","4","5","6","7","8","9","10","11","12","13","14","15","16","17","18","19","20","21","22","23","24","25","26","27","28","29","30","31","32","33","34","35","36","37","38","39","40"],["A","A","B","B","C","C","D","D","E","E","F","F","G","G","H","H","I","I","J","J","K","K","L","L","M","M","N","N","O","O","P","P","Q","Q","R","R","S","S","T","T"],["NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES"],[2227,3458,4870,2707,2773,4750,2475,2122,4280,3293,3271,3521,2950,4159,4517,3988,2512,2799,4496,4425,4716,3547,3998,2827,2427,3989,2358,4197,2987,3130,2275,3597,3607,4499,2796,2193,4631,2492,4303,2233],[1134,1576,1510,1279,1224,581,1242,700,1529,624,1584,1471,202,1211,1726,1255,1855,616,1834,1953,987,1441,798,1542,550,1715,1100,1047,1777,1929,543,735,1688,1683,345,1601,1420,1333,1229,958],[1502,1327,1647,1188,1430,1768,806,1875,565,1024,528,1258,603,490,935,438,301,1751,1161,1276,1606,1665,376,783,1143,1560,1571,663,697,1596,726,1128,313,1410,1020,1444,1935,1816,1346,912],[0.39,0.02,0.19,0.29,0.54,0.03,0.04,0.36,0.47,0.38,0.69,0.65,0.46,0.2,0.26,0.77,0.86,0.59,0.22,0.34,0.63,0.83,0.89,0.42,0.94,0.45,0.95,0.58,0.01,0.28,0.32,0.96,0.07,0.76,0.13,0.05,0.85,0.75,0.31,0.23],[-0.02,0.01,0.28,0.12,0.32,0,-0.5,-0.01,0.27,0.24,-0.11,-0.4,-0.06,0.31,0.15,0.41,0.42,-0.05,-0.16,-0.48,0.18,-0.45,0.05,0.02,0.43,0.04,-0.46,-0.25,-0.14,0.37,0.16,-0.34,-0.32,0.44,0.26,-0.43,-0.13,-0.42,-0.09,-0.2]],"container":"<table class=\"display\">\n  <thead>\n    <tr>\n      <th> <\/th>\n      <th>type1<\/th>\n      <th>type2<\/th>\n      <th>value<\/th>\n      <th>value1<\/th>\n      <th>value2<\/th>\n      <th>prob1<\/th>\n      <th>prob2<\/th>\n    <\/tr>\n  <\/thead>\n<\/table>","options":{"pageLength":5,"dom":"ftip","initComplete":"function(settings, json) {\n    $(this.api().tables().body()).css({'color': 'red', 'font-size':'14px'});\n    }","columnDefs":[{"className":"dt-right","targets":[3,4,5,6,7]},{"orderable":false,"targets":0}],"order":[],"autoWidth":false,"orderClasses":false,"lengthMenu":[5,10,25,50,100]}},"evals":["options.initComplete"],"jsHooks":[]}</script>

-   表头与表格主体。

``` r
datatable(data, options = list(
  initComplete = JS(
    "function(settings, json) {
    $(this.api().table().header()).css({'background-color': 'black', 'color': 'green','font-size':'18px'});
    $(this.api().tables().body()).css({'color': 'red','font-size':'14px'});
    }")
))
```

<div id="htmlwidget-27" style="width:100%;height:auto;" class="datatables html-widget"></div>
<script type="application/json" data-for="htmlwidget-27">{"x":{"filter":"none","vertical":false,"data":[["1","2","3","4","5","6","7","8","9","10","11","12","13","14","15","16","17","18","19","20","21","22","23","24","25","26","27","28","29","30","31","32","33","34","35","36","37","38","39","40"],["A","A","B","B","C","C","D","D","E","E","F","F","G","G","H","H","I","I","J","J","K","K","L","L","M","M","N","N","O","O","P","P","Q","Q","R","R","S","S","T","T"],["NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES"],[2227,3458,4870,2707,2773,4750,2475,2122,4280,3293,3271,3521,2950,4159,4517,3988,2512,2799,4496,4425,4716,3547,3998,2827,2427,3989,2358,4197,2987,3130,2275,3597,3607,4499,2796,2193,4631,2492,4303,2233],[1134,1576,1510,1279,1224,581,1242,700,1529,624,1584,1471,202,1211,1726,1255,1855,616,1834,1953,987,1441,798,1542,550,1715,1100,1047,1777,1929,543,735,1688,1683,345,1601,1420,1333,1229,958],[1502,1327,1647,1188,1430,1768,806,1875,565,1024,528,1258,603,490,935,438,301,1751,1161,1276,1606,1665,376,783,1143,1560,1571,663,697,1596,726,1128,313,1410,1020,1444,1935,1816,1346,912],[0.39,0.02,0.19,0.29,0.54,0.03,0.04,0.36,0.47,0.38,0.69,0.65,0.46,0.2,0.26,0.77,0.86,0.59,0.22,0.34,0.63,0.83,0.89,0.42,0.94,0.45,0.95,0.58,0.01,0.28,0.32,0.96,0.07,0.76,0.13,0.05,0.85,0.75,0.31,0.23],[-0.02,0.01,0.28,0.12,0.32,0,-0.5,-0.01,0.27,0.24,-0.11,-0.4,-0.06,0.31,0.15,0.41,0.42,-0.05,-0.16,-0.48,0.18,-0.45,0.05,0.02,0.43,0.04,-0.46,-0.25,-0.14,0.37,0.16,-0.34,-0.32,0.44,0.26,-0.43,-0.13,-0.42,-0.09,-0.2]],"container":"<table class=\"display\">\n  <thead>\n    <tr>\n      <th> <\/th>\n      <th>type1<\/th>\n      <th>type2<\/th>\n      <th>value<\/th>\n      <th>value1<\/th>\n      <th>value2<\/th>\n      <th>prob1<\/th>\n      <th>prob2<\/th>\n    <\/tr>\n  <\/thead>\n<\/table>","options":{"pageLength":5,"dom":"ftip","initComplete":"function(settings, json) {\n    $(this.api().table().header()).css({'background-color': 'black', 'color': 'green','font-size':'18px'});\n    $(this.api().tables().body()).css({'color': 'red','font-size':'14px'});\n    }","columnDefs":[{"className":"dt-right","targets":[3,4,5,6,7]},{"orderable":false,"targets":0}],"order":[],"autoWidth":false,"orderClasses":false,"lengthMenu":[5,10,25,50,100]}},"evals":["options.initComplete"],"jsHooks":[]}</script>

-   仅保留表格主体。

``` r
datatable(data,
          options = list(
            initComplete = JS(
              "function(settings, json) {
    $(this.api().table().header()).css({'display': 'none'});
    $('table.dataTable.no-footer').css('border-bottom', 'none');
    }")))
```

<div id="htmlwidget-28" style="width:100%;height:auto;" class="datatables html-widget"></div>
<script type="application/json" data-for="htmlwidget-28">{"x":{"filter":"none","vertical":false,"data":[["1","2","3","4","5","6","7","8","9","10","11","12","13","14","15","16","17","18","19","20","21","22","23","24","25","26","27","28","29","30","31","32","33","34","35","36","37","38","39","40"],["A","A","B","B","C","C","D","D","E","E","F","F","G","G","H","H","I","I","J","J","K","K","L","L","M","M","N","N","O","O","P","P","Q","Q","R","R","S","S","T","T"],["NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES"],[2227,3458,4870,2707,2773,4750,2475,2122,4280,3293,3271,3521,2950,4159,4517,3988,2512,2799,4496,4425,4716,3547,3998,2827,2427,3989,2358,4197,2987,3130,2275,3597,3607,4499,2796,2193,4631,2492,4303,2233],[1134,1576,1510,1279,1224,581,1242,700,1529,624,1584,1471,202,1211,1726,1255,1855,616,1834,1953,987,1441,798,1542,550,1715,1100,1047,1777,1929,543,735,1688,1683,345,1601,1420,1333,1229,958],[1502,1327,1647,1188,1430,1768,806,1875,565,1024,528,1258,603,490,935,438,301,1751,1161,1276,1606,1665,376,783,1143,1560,1571,663,697,1596,726,1128,313,1410,1020,1444,1935,1816,1346,912],[0.39,0.02,0.19,0.29,0.54,0.03,0.04,0.36,0.47,0.38,0.69,0.65,0.46,0.2,0.26,0.77,0.86,0.59,0.22,0.34,0.63,0.83,0.89,0.42,0.94,0.45,0.95,0.58,0.01,0.28,0.32,0.96,0.07,0.76,0.13,0.05,0.85,0.75,0.31,0.23],[-0.02,0.01,0.28,0.12,0.32,0,-0.5,-0.01,0.27,0.24,-0.11,-0.4,-0.06,0.31,0.15,0.41,0.42,-0.05,-0.16,-0.48,0.18,-0.45,0.05,0.02,0.43,0.04,-0.46,-0.25,-0.14,0.37,0.16,-0.34,-0.32,0.44,0.26,-0.43,-0.13,-0.42,-0.09,-0.2]],"container":"<table class=\"display\">\n  <thead>\n    <tr>\n      <th> <\/th>\n      <th>type1<\/th>\n      <th>type2<\/th>\n      <th>value<\/th>\n      <th>value1<\/th>\n      <th>value2<\/th>\n      <th>prob1<\/th>\n      <th>prob2<\/th>\n    <\/tr>\n  <\/thead>\n<\/table>","options":{"pageLength":5,"dom":"ftip","initComplete":"function(settings, json) {\n    $(this.api().table().header()).css({'display': 'none'});\n    $('table.dataTable.no-footer').css('border-bottom', 'none');\n    }","columnDefs":[{"className":"dt-right","targets":[3,4,5,6,7]},{"orderable":false,"targets":0}],"order":[],"autoWidth":false,"orderClasses":false,"lengthMenu":[5,10,25,50,100]}},"evals":["options.initComplete"],"jsHooks":[]}</script>

-   单列的表头，`column(3).header()` 表示第三列的表头。

``` r
datatable(data,
          options = list(
            initComplete = JS(
              "function(settings, json) {
    $(this.api().column(3).header()).css({'background-color': 'black', 'color': 'green','font-size':'18px'});
    }")))
```

<div id="htmlwidget-29" style="width:100%;height:auto;" class="datatables html-widget"></div>
<script type="application/json" data-for="htmlwidget-29">{"x":{"filter":"none","vertical":false,"data":[["1","2","3","4","5","6","7","8","9","10","11","12","13","14","15","16","17","18","19","20","21","22","23","24","25","26","27","28","29","30","31","32","33","34","35","36","37","38","39","40"],["A","A","B","B","C","C","D","D","E","E","F","F","G","G","H","H","I","I","J","J","K","K","L","L","M","M","N","N","O","O","P","P","Q","Q","R","R","S","S","T","T"],["NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES"],[2227,3458,4870,2707,2773,4750,2475,2122,4280,3293,3271,3521,2950,4159,4517,3988,2512,2799,4496,4425,4716,3547,3998,2827,2427,3989,2358,4197,2987,3130,2275,3597,3607,4499,2796,2193,4631,2492,4303,2233],[1134,1576,1510,1279,1224,581,1242,700,1529,624,1584,1471,202,1211,1726,1255,1855,616,1834,1953,987,1441,798,1542,550,1715,1100,1047,1777,1929,543,735,1688,1683,345,1601,1420,1333,1229,958],[1502,1327,1647,1188,1430,1768,806,1875,565,1024,528,1258,603,490,935,438,301,1751,1161,1276,1606,1665,376,783,1143,1560,1571,663,697,1596,726,1128,313,1410,1020,1444,1935,1816,1346,912],[0.39,0.02,0.19,0.29,0.54,0.03,0.04,0.36,0.47,0.38,0.69,0.65,0.46,0.2,0.26,0.77,0.86,0.59,0.22,0.34,0.63,0.83,0.89,0.42,0.94,0.45,0.95,0.58,0.01,0.28,0.32,0.96,0.07,0.76,0.13,0.05,0.85,0.75,0.31,0.23],[-0.02,0.01,0.28,0.12,0.32,0,-0.5,-0.01,0.27,0.24,-0.11,-0.4,-0.06,0.31,0.15,0.41,0.42,-0.05,-0.16,-0.48,0.18,-0.45,0.05,0.02,0.43,0.04,-0.46,-0.25,-0.14,0.37,0.16,-0.34,-0.32,0.44,0.26,-0.43,-0.13,-0.42,-0.09,-0.2]],"container":"<table class=\"display\">\n  <thead>\n    <tr>\n      <th> <\/th>\n      <th>type1<\/th>\n      <th>type2<\/th>\n      <th>value<\/th>\n      <th>value1<\/th>\n      <th>value2<\/th>\n      <th>prob1<\/th>\n      <th>prob2<\/th>\n    <\/tr>\n  <\/thead>\n<\/table>","options":{"pageLength":5,"dom":"ftip","initComplete":"function(settings, json) {\n    $(this.api().column(3).header()).css({'background-color': 'black', 'color': 'green','font-size':'18px'});\n    }","columnDefs":[{"className":"dt-right","targets":[3,4,5,6,7]},{"orderable":false,"targets":0}],"order":[],"autoWidth":false,"orderClasses":false,"lengthMenu":[5,10,25,50,100]}},"evals":["options.initComplete"],"jsHooks":[]}</script>

-   单列的单元格，`column(3).nodes()` 表示第三列的单元格。

``` r
datatable(data,
          options = list(
            initComplete = JS(
              "function(settings, json) {
    $(this.api().column(3).nodes()).css({'color': 'red','font-size':'14px'});
    }")))
```

<div id="htmlwidget-30" style="width:100%;height:auto;" class="datatables html-widget"></div>
<script type="application/json" data-for="htmlwidget-30">{"x":{"filter":"none","vertical":false,"data":[["1","2","3","4","5","6","7","8","9","10","11","12","13","14","15","16","17","18","19","20","21","22","23","24","25","26","27","28","29","30","31","32","33","34","35","36","37","38","39","40"],["A","A","B","B","C","C","D","D","E","E","F","F","G","G","H","H","I","I","J","J","K","K","L","L","M","M","N","N","O","O","P","P","Q","Q","R","R","S","S","T","T"],["NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES"],[2227,3458,4870,2707,2773,4750,2475,2122,4280,3293,3271,3521,2950,4159,4517,3988,2512,2799,4496,4425,4716,3547,3998,2827,2427,3989,2358,4197,2987,3130,2275,3597,3607,4499,2796,2193,4631,2492,4303,2233],[1134,1576,1510,1279,1224,581,1242,700,1529,624,1584,1471,202,1211,1726,1255,1855,616,1834,1953,987,1441,798,1542,550,1715,1100,1047,1777,1929,543,735,1688,1683,345,1601,1420,1333,1229,958],[1502,1327,1647,1188,1430,1768,806,1875,565,1024,528,1258,603,490,935,438,301,1751,1161,1276,1606,1665,376,783,1143,1560,1571,663,697,1596,726,1128,313,1410,1020,1444,1935,1816,1346,912],[0.39,0.02,0.19,0.29,0.54,0.03,0.04,0.36,0.47,0.38,0.69,0.65,0.46,0.2,0.26,0.77,0.86,0.59,0.22,0.34,0.63,0.83,0.89,0.42,0.94,0.45,0.95,0.58,0.01,0.28,0.32,0.96,0.07,0.76,0.13,0.05,0.85,0.75,0.31,0.23],[-0.02,0.01,0.28,0.12,0.32,0,-0.5,-0.01,0.27,0.24,-0.11,-0.4,-0.06,0.31,0.15,0.41,0.42,-0.05,-0.16,-0.48,0.18,-0.45,0.05,0.02,0.43,0.04,-0.46,-0.25,-0.14,0.37,0.16,-0.34,-0.32,0.44,0.26,-0.43,-0.13,-0.42,-0.09,-0.2]],"container":"<table class=\"display\">\n  <thead>\n    <tr>\n      <th> <\/th>\n      <th>type1<\/th>\n      <th>type2<\/th>\n      <th>value<\/th>\n      <th>value1<\/th>\n      <th>value2<\/th>\n      <th>prob1<\/th>\n      <th>prob2<\/th>\n    <\/tr>\n  <\/thead>\n<\/table>","options":{"pageLength":5,"dom":"ftip","initComplete":"function(settings, json) {\n    $(this.api().column(3).nodes()).css({'color': 'red','font-size':'14px'});\n    }","columnDefs":[{"className":"dt-right","targets":[3,4,5,6,7]},{"orderable":false,"targets":0}],"order":[],"autoWidth":false,"orderClasses":false,"lengthMenu":[5,10,25,50,100]}},"evals":["options.initComplete"],"jsHooks":[]}</script>

### 1.5.2.列渲染（columnDefs.render）

通过列渲染的方式引入 JS 也可以设置目标列的 css 样式。需要注意的是，此方法的本质是通过 JS 函数引入 html 元素，再引入 css 来设定样式，具体呈现效果与元素本身的特性息息相关。如下面例子中使用 div 元素设定边框样式，本质是在表格的单元格中把原来的数据用一个框框起来，一般情况下边框不会把表格沾满，设置的左边框线也不会是连续的。而 span 元素本身是用来组合文本的，在这种情况下设定边框样式，边框线会紧紧贴着文本。

本小节引入的类名 ‘border-left’ 和 ‘color’ 源于第1.3.3小节。

``` r
datatable(data,
          options = list(columnDefs = list(
            list(
              targets = 3,
              render = JS(
                "function(data, type, row, meta){
              return '<div class=\"border-left\">' + data + '</div>'
              }"
              )
            ),
            list(
              targets = 4,
              render = JS(
                "function(data, type, row, meta){
              return '<div class=\"color\">' + data + '</div>'
              }"
              )
            ),
            list(
              targets = 5,
              render = JS(
                "function(data, type, row, meta){
              return '<span class=\"border-left\">' + data + '</span>'
              }"
              )
            )
          )))
```

<div id="htmlwidget-31" style="width:100%;height:auto;" class="datatables html-widget"></div>
<script type="application/json" data-for="htmlwidget-31">{"x":{"filter":"none","vertical":false,"data":[["1","2","3","4","5","6","7","8","9","10","11","12","13","14","15","16","17","18","19","20","21","22","23","24","25","26","27","28","29","30","31","32","33","34","35","36","37","38","39","40"],["A","A","B","B","C","C","D","D","E","E","F","F","G","G","H","H","I","I","J","J","K","K","L","L","M","M","N","N","O","O","P","P","Q","Q","R","R","S","S","T","T"],["NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES"],[2227,3458,4870,2707,2773,4750,2475,2122,4280,3293,3271,3521,2950,4159,4517,3988,2512,2799,4496,4425,4716,3547,3998,2827,2427,3989,2358,4197,2987,3130,2275,3597,3607,4499,2796,2193,4631,2492,4303,2233],[1134,1576,1510,1279,1224,581,1242,700,1529,624,1584,1471,202,1211,1726,1255,1855,616,1834,1953,987,1441,798,1542,550,1715,1100,1047,1777,1929,543,735,1688,1683,345,1601,1420,1333,1229,958],[1502,1327,1647,1188,1430,1768,806,1875,565,1024,528,1258,603,490,935,438,301,1751,1161,1276,1606,1665,376,783,1143,1560,1571,663,697,1596,726,1128,313,1410,1020,1444,1935,1816,1346,912],[0.39,0.02,0.19,0.29,0.54,0.03,0.04,0.36,0.47,0.38,0.69,0.65,0.46,0.2,0.26,0.77,0.86,0.59,0.22,0.34,0.63,0.83,0.89,0.42,0.94,0.45,0.95,0.58,0.01,0.28,0.32,0.96,0.07,0.76,0.13,0.05,0.85,0.75,0.31,0.23],[-0.02,0.01,0.28,0.12,0.32,0,-0.5,-0.01,0.27,0.24,-0.11,-0.4,-0.06,0.31,0.15,0.41,0.42,-0.05,-0.16,-0.48,0.18,-0.45,0.05,0.02,0.43,0.04,-0.46,-0.25,-0.14,0.37,0.16,-0.34,-0.32,0.44,0.26,-0.43,-0.13,-0.42,-0.09,-0.2]],"container":"<table class=\"display\">\n  <thead>\n    <tr>\n      <th> <\/th>\n      <th>type1<\/th>\n      <th>type2<\/th>\n      <th>value<\/th>\n      <th>value1<\/th>\n      <th>value2<\/th>\n      <th>prob1<\/th>\n      <th>prob2<\/th>\n    <\/tr>\n  <\/thead>\n<\/table>","options":{"pageLength":5,"dom":"ftip","columnDefs":[{"targets":3,"render":"function(data, type, row, meta){\n              return '<div class=\"border-left\">' + data + '<\/div>'\n              }"},{"targets":4,"render":"function(data, type, row, meta){\n              return '<div class=\"color\">' + data + '<\/div>'\n              }"},{"targets":5,"render":"function(data, type, row, meta){\n              return '<span class=\"border-left\">' + data + '<\/span>'\n              }"},{"className":"dt-right","targets":[3,4,5,6,7]},{"orderable":false,"targets":0}],"order":[],"autoWidth":false,"orderClasses":false,"lengthMenu":[5,10,25,50,100]}},"evals":["options.columnDefs.0.render","options.columnDefs.1.render","options.columnDefs.2.render"],"jsHooks":[]}</script>

## 1.6.数据格式

### 1.6.1.添加特殊符号

-   `formatCurrency()`：为表格中的数值列添加货币符号（UNICODE 编码对应的符号），或者字符串。

    -   columns：指定格式化的一列或者多列，可以填入代表列序号的数字或者列名称。填入列名称时，须填入数据中的原始列名，填入重命名后的列名无效。
    -   interval：填入一个数字，当数字每间隔多少位后添加一个标记，默认为3。
    -   mark：指定间隔符号，默认“,”。
    -   zero.print：填入一个字符串，替换数字列中的0，默认为 NULL。
    -   currency：填入适用于 JS 的 [UNICODE 编码](https://www.cnblogs.com/lsgxeva/p/10120275.html)，或者一个普通的字符串。如填入`\U20AC`，显示为€；填入`\u21AC`，显示为↬；填入`\u2714`，显示为✔。
    -   before：指定填入的符号是否放在数字前面，默认参数值为 TRUE。
    -   digits：当目标列为数值时，指定小数点后位数，默认保留2位。
    -   rows：指定目标列中的目标行。

``` r
datatable(data) |>
  formatCurrency(
    columns = c('value', 'value1'),
    currency = '\u2714',
    before = FALSE, 
    digits = 0, 
    rows = c(1:2) 
  ) |>
  formatCurrency(
    columns = 6,
    currency = '%',
    before = FALSE,
    digits = 2,
    rows = c(3:5)
  )
```

<div id="htmlwidget-32" style="width:100%;height:auto;" class="datatables html-widget"></div>
<script type="application/json" data-for="htmlwidget-32">{"x":{"filter":"none","vertical":false,"data":[["1","2","3","4","5","6","7","8","9","10","11","12","13","14","15","16","17","18","19","20","21","22","23","24","25","26","27","28","29","30","31","32","33","34","35","36","37","38","39","40"],["A","A","B","B","C","C","D","D","E","E","F","F","G","G","H","H","I","I","J","J","K","K","L","L","M","M","N","N","O","O","P","P","Q","Q","R","R","S","S","T","T"],["NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES"],[2227,3458,4870,2707,2773,4750,2475,2122,4280,3293,3271,3521,2950,4159,4517,3988,2512,2799,4496,4425,4716,3547,3998,2827,2427,3989,2358,4197,2987,3130,2275,3597,3607,4499,2796,2193,4631,2492,4303,2233],[1134,1576,1510,1279,1224,581,1242,700,1529,624,1584,1471,202,1211,1726,1255,1855,616,1834,1953,987,1441,798,1542,550,1715,1100,1047,1777,1929,543,735,1688,1683,345,1601,1420,1333,1229,958],[1502,1327,1647,1188,1430,1768,806,1875,565,1024,528,1258,603,490,935,438,301,1751,1161,1276,1606,1665,376,783,1143,1560,1571,663,697,1596,726,1128,313,1410,1020,1444,1935,1816,1346,912],[0.39,0.02,0.19,0.29,0.54,0.03,0.04,0.36,0.47,0.38,0.69,0.65,0.46,0.2,0.26,0.77,0.86,0.59,0.22,0.34,0.63,0.83,0.89,0.42,0.94,0.45,0.95,0.58,0.01,0.28,0.32,0.96,0.07,0.76,0.13,0.05,0.85,0.75,0.31,0.23],[-0.02,0.01,0.28,0.12,0.32,0,-0.5,-0.01,0.27,0.24,-0.11,-0.4,-0.06,0.31,0.15,0.41,0.42,-0.05,-0.16,-0.48,0.18,-0.45,0.05,0.02,0.43,0.04,-0.46,-0.25,-0.14,0.37,0.16,-0.34,-0.32,0.44,0.26,-0.43,-0.13,-0.42,-0.09,-0.2]],"container":"<table class=\"display\">\n  <thead>\n    <tr>\n      <th> <\/th>\n      <th>type1<\/th>\n      <th>type2<\/th>\n      <th>value<\/th>\n      <th>value1<\/th>\n      <th>value2<\/th>\n      <th>prob1<\/th>\n      <th>prob2<\/th>\n    <\/tr>\n  <\/thead>\n<\/table>","options":{"pageLength":5,"dom":"ftip","columnDefs":[{"targets":6,"render":"function(data, type, row, meta) {\n    return type !== 'display' || $.inArray(meta.row + 1, [3,4,5]) < 0 ? data : DTWidget.formatCurrency(data, \"%\", 2, 3, \",\", \".\", false, null);\n  }"},{"targets":3,"render":"function(data, type, row, meta) {\n    return type !== 'display' || $.inArray(meta.row + 1, [1,2]) < 0 ? data : DTWidget.formatCurrency(data, \"✔\", 0, 3, \",\", \".\", false, null);\n  }"},{"targets":4,"render":"function(data, type, row, meta) {\n    return type !== 'display' || $.inArray(meta.row + 1, [1,2]) < 0 ? data : DTWidget.formatCurrency(data, \"✔\", 0, 3, \",\", \".\", false, null);\n  }"},{"className":"dt-right","targets":[3,4,5,6,7]},{"orderable":false,"targets":0}],"order":[],"autoWidth":false,"orderClasses":false,"lengthMenu":[5,10,25,50,100]}},"evals":["options.columnDefs.0.render","options.columnDefs.1.render","options.columnDefs.2.render"],"jsHooks":[]}</script>

-   `formatString(table, columns, prefix = "", suffix = "", rows = NULL)`。

    -   prefix/suffix：填入放在一列数据之前、之后的字符串，同 `formatCurrency()`函数中的 currency 参数一样，除了可以填入普通的字符串，还可以填入 UNICODE 编码来展示特殊字符。

``` r
datatable(data) |>
  formatString(
    columns = 3,
    prefix = '￥',
    suffix = '\u2716',
    rows = seq(
      from = 1,
      to = nrow(data),
      by = 2
    )
  )
```

<div id="htmlwidget-33" style="width:100%;height:auto;" class="datatables html-widget"></div>
<script type="application/json" data-for="htmlwidget-33">{"x":{"filter":"none","vertical":false,"data":[["1","2","3","4","5","6","7","8","9","10","11","12","13","14","15","16","17","18","19","20","21","22","23","24","25","26","27","28","29","30","31","32","33","34","35","36","37","38","39","40"],["A","A","B","B","C","C","D","D","E","E","F","F","G","G","H","H","I","I","J","J","K","K","L","L","M","M","N","N","O","O","P","P","Q","Q","R","R","S","S","T","T"],["NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES"],[2227,3458,4870,2707,2773,4750,2475,2122,4280,3293,3271,3521,2950,4159,4517,3988,2512,2799,4496,4425,4716,3547,3998,2827,2427,3989,2358,4197,2987,3130,2275,3597,3607,4499,2796,2193,4631,2492,4303,2233],[1134,1576,1510,1279,1224,581,1242,700,1529,624,1584,1471,202,1211,1726,1255,1855,616,1834,1953,987,1441,798,1542,550,1715,1100,1047,1777,1929,543,735,1688,1683,345,1601,1420,1333,1229,958],[1502,1327,1647,1188,1430,1768,806,1875,565,1024,528,1258,603,490,935,438,301,1751,1161,1276,1606,1665,376,783,1143,1560,1571,663,697,1596,726,1128,313,1410,1020,1444,1935,1816,1346,912],[0.39,0.02,0.19,0.29,0.54,0.03,0.04,0.36,0.47,0.38,0.69,0.65,0.46,0.2,0.26,0.77,0.86,0.59,0.22,0.34,0.63,0.83,0.89,0.42,0.94,0.45,0.95,0.58,0.01,0.28,0.32,0.96,0.07,0.76,0.13,0.05,0.85,0.75,0.31,0.23],[-0.02,0.01,0.28,0.12,0.32,0,-0.5,-0.01,0.27,0.24,-0.11,-0.4,-0.06,0.31,0.15,0.41,0.42,-0.05,-0.16,-0.48,0.18,-0.45,0.05,0.02,0.43,0.04,-0.46,-0.25,-0.14,0.37,0.16,-0.34,-0.32,0.44,0.26,-0.43,-0.13,-0.42,-0.09,-0.2]],"container":"<table class=\"display\">\n  <thead>\n    <tr>\n      <th> <\/th>\n      <th>type1<\/th>\n      <th>type2<\/th>\n      <th>value<\/th>\n      <th>value1<\/th>\n      <th>value2<\/th>\n      <th>prob1<\/th>\n      <th>prob2<\/th>\n    <\/tr>\n  <\/thead>\n<\/table>","options":{"pageLength":5,"dom":"ftip","columnDefs":[{"targets":3,"render":"function(data, type, row, meta) {\n    return type !== 'display' || $.inArray(meta.row + 1, [1,3,5,7,9,11,13,15,17,19,21,23,25,27,29,31,33,35,37,39]) < 0 ? data : DTWidget.formatString(data, \"￥\", \"✖\");\n  }"},{"className":"dt-right","targets":[3,4,5,6,7]},{"orderable":false,"targets":0}],"order":[],"autoWidth":false,"orderClasses":false,"lengthMenu":[5,10,25,50,100]}},"evals":["options.columnDefs.0.render"],"jsHooks":[]}</script>

### 1.6.2.转换数据格式

-   `formatPercentage()`：将表格中目标列的数值格式化为百分比。

    -   columns/interval/mark/zero.print/digits/rows：与 `formatCurrency()`一致。

``` r
datatable(data) |>
  formatPercentage(columns = c(6,7),
                   digits = 1,
                   rows = c(1, 2))
```

<div id="htmlwidget-34" style="width:100%;height:auto;" class="datatables html-widget"></div>
<script type="application/json" data-for="htmlwidget-34">{"x":{"filter":"none","vertical":false,"data":[["1","2","3","4","5","6","7","8","9","10","11","12","13","14","15","16","17","18","19","20","21","22","23","24","25","26","27","28","29","30","31","32","33","34","35","36","37","38","39","40"],["A","A","B","B","C","C","D","D","E","E","F","F","G","G","H","H","I","I","J","J","K","K","L","L","M","M","N","N","O","O","P","P","Q","Q","R","R","S","S","T","T"],["NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES"],[2227,3458,4870,2707,2773,4750,2475,2122,4280,3293,3271,3521,2950,4159,4517,3988,2512,2799,4496,4425,4716,3547,3998,2827,2427,3989,2358,4197,2987,3130,2275,3597,3607,4499,2796,2193,4631,2492,4303,2233],[1134,1576,1510,1279,1224,581,1242,700,1529,624,1584,1471,202,1211,1726,1255,1855,616,1834,1953,987,1441,798,1542,550,1715,1100,1047,1777,1929,543,735,1688,1683,345,1601,1420,1333,1229,958],[1502,1327,1647,1188,1430,1768,806,1875,565,1024,528,1258,603,490,935,438,301,1751,1161,1276,1606,1665,376,783,1143,1560,1571,663,697,1596,726,1128,313,1410,1020,1444,1935,1816,1346,912],[0.39,0.02,0.19,0.29,0.54,0.03,0.04,0.36,0.47,0.38,0.69,0.65,0.46,0.2,0.26,0.77,0.86,0.59,0.22,0.34,0.63,0.83,0.89,0.42,0.94,0.45,0.95,0.58,0.01,0.28,0.32,0.96,0.07,0.76,0.13,0.05,0.85,0.75,0.31,0.23],[-0.02,0.01,0.28,0.12,0.32,0,-0.5,-0.01,0.27,0.24,-0.11,-0.4,-0.06,0.31,0.15,0.41,0.42,-0.05,-0.16,-0.48,0.18,-0.45,0.05,0.02,0.43,0.04,-0.46,-0.25,-0.14,0.37,0.16,-0.34,-0.32,0.44,0.26,-0.43,-0.13,-0.42,-0.09,-0.2]],"container":"<table class=\"display\">\n  <thead>\n    <tr>\n      <th> <\/th>\n      <th>type1<\/th>\n      <th>type2<\/th>\n      <th>value<\/th>\n      <th>value1<\/th>\n      <th>value2<\/th>\n      <th>prob1<\/th>\n      <th>prob2<\/th>\n    <\/tr>\n  <\/thead>\n<\/table>","options":{"pageLength":5,"dom":"ftip","columnDefs":[{"targets":6,"render":"function(data, type, row, meta) {\n    return type !== 'display' || $.inArray(meta.row + 1, [1,2]) < 0 ? data : DTWidget.formatPercentage(data, 1, 3, \",\", \".\", null);\n  }"},{"targets":7,"render":"function(data, type, row, meta) {\n    return type !== 'display' || $.inArray(meta.row + 1, [1,2]) < 0 ? data : DTWidget.formatPercentage(data, 1, 3, \",\", \".\", null);\n  }"},{"className":"dt-right","targets":[3,4,5,6,7]},{"orderable":false,"targets":0}],"order":[],"autoWidth":false,"orderClasses":false,"lengthMenu":[5,10,25,50,100]}},"evals":["options.columnDefs.0.render","options.columnDefs.1.render"],"jsHooks":[]}</script>

-   `formatRound()`：将表格中的目标列的数值四舍五入到指定的小数位数。

    -   columns/interval/mark/zero.print/digits/rows：与 `formatCurrency()`一致。

``` r
data1 <- data
set.seed(2022)
data1$value3 <- runif(nrow(data), 0.0, 1.0)

datatable(data1) |>
  formatRound(columns = 'value3',
              digits = 2,
              row = c(1:2))
```

<div id="htmlwidget-35" style="width:100%;height:auto;" class="datatables html-widget"></div>
<script type="application/json" data-for="htmlwidget-35">{"x":{"filter":"none","vertical":false,"data":[["1","2","3","4","5","6","7","8","9","10","11","12","13","14","15","16","17","18","19","20","21","22","23","24","25","26","27","28","29","30","31","32","33","34","35","36","37","38","39","40"],["A","A","B","B","C","C","D","D","E","E","F","F","G","G","H","H","I","I","J","J","K","K","L","L","M","M","N","N","O","O","P","P","Q","Q","R","R","S","S","T","T"],["NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES"],[2227,3458,4870,2707,2773,4750,2475,2122,4280,3293,3271,3521,2950,4159,4517,3988,2512,2799,4496,4425,4716,3547,3998,2827,2427,3989,2358,4197,2987,3130,2275,3597,3607,4499,2796,2193,4631,2492,4303,2233],[1134,1576,1510,1279,1224,581,1242,700,1529,624,1584,1471,202,1211,1726,1255,1855,616,1834,1953,987,1441,798,1542,550,1715,1100,1047,1777,1929,543,735,1688,1683,345,1601,1420,1333,1229,958],[1502,1327,1647,1188,1430,1768,806,1875,565,1024,528,1258,603,490,935,438,301,1751,1161,1276,1606,1665,376,783,1143,1560,1571,663,697,1596,726,1128,313,1410,1020,1444,1935,1816,1346,912],[0.39,0.02,0.19,0.29,0.54,0.03,0.04,0.36,0.47,0.38,0.69,0.65,0.46,0.2,0.26,0.77,0.86,0.59,0.22,0.34,0.63,0.83,0.89,0.42,0.94,0.45,0.95,0.58,0.01,0.28,0.32,0.96,0.07,0.76,0.13,0.05,0.85,0.75,0.31,0.23],[-0.02,0.01,0.28,0.12,0.32,0,-0.5,-0.01,0.27,0.24,-0.11,-0.4,-0.06,0.31,0.15,0.41,0.42,-0.05,-0.16,-0.48,0.18,-0.45,0.05,0.02,0.43,0.04,-0.46,-0.25,-0.14,0.37,0.16,-0.34,-0.32,0.44,0.26,-0.43,-0.13,-0.42,-0.09,-0.2],[0.81597765465267,0.647259329678491,0.120328583521768,0.543800154002383,0.184729989385232,0.635790845612064,0.0742989955469966,0.0419759317301214,0.370317112421617,0.757252902723849,0.00186207285150886,0.159799489425495,0.144741663709283,0.519396774005145,0.609476454323158,0.122510588727891,0.773217808688059,0.514508979162201,0.595448171719909,0.850909892003983,0.842836875235662,0.570326561806723,0.426557252649218,0.137205496430397,0.163092608796433,0.93508125981316,0.537011651322246,0.997654764913023,0.478951843688264,0.773609737167135,0.467988230520859,0.637632509926334,0.256522512063384,0.405364905018359,0.17088253586553,0.0679756663739681,0.846031822729856,0.549878273857757,0.804842539597303,0.765064378036186]],"container":"<table class=\"display\">\n  <thead>\n    <tr>\n      <th> <\/th>\n      <th>type1<\/th>\n      <th>type2<\/th>\n      <th>value<\/th>\n      <th>value1<\/th>\n      <th>value2<\/th>\n      <th>prob1<\/th>\n      <th>prob2<\/th>\n      <th>value3<\/th>\n    <\/tr>\n  <\/thead>\n<\/table>","options":{"pageLength":5,"dom":"ftip","columnDefs":[{"targets":8,"render":"function(data, type, row, meta) {\n    return type !== 'display' || $.inArray(meta.row + 1, [1,2]) < 0 ? data : DTWidget.formatRound(data, 2, 3, \",\", \".\", null);\n  }"},{"className":"dt-right","targets":[3,4,5,6,7,8]},{"orderable":false,"targets":0}],"order":[],"autoWidth":false,"orderClasses":false,"lengthMenu":[5,10,25,50,100]}},"evals":["options.columnDefs.0.render"],"jsHooks":[]}</script>

-   `formatSignif()`：指定小数点后有效数字的位数。

    -   columns/interval/mark/zero.print/digits/rows：与 `formatCurrency()`一致。

``` r
datatable(data1) |>
  formatSignif('value3', 3)
```

<div id="htmlwidget-36" style="width:100%;height:auto;" class="datatables html-widget"></div>
<script type="application/json" data-for="htmlwidget-36">{"x":{"filter":"none","vertical":false,"data":[["1","2","3","4","5","6","7","8","9","10","11","12","13","14","15","16","17","18","19","20","21","22","23","24","25","26","27","28","29","30","31","32","33","34","35","36","37","38","39","40"],["A","A","B","B","C","C","D","D","E","E","F","F","G","G","H","H","I","I","J","J","K","K","L","L","M","M","N","N","O","O","P","P","Q","Q","R","R","S","S","T","T"],["NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES"],[2227,3458,4870,2707,2773,4750,2475,2122,4280,3293,3271,3521,2950,4159,4517,3988,2512,2799,4496,4425,4716,3547,3998,2827,2427,3989,2358,4197,2987,3130,2275,3597,3607,4499,2796,2193,4631,2492,4303,2233],[1134,1576,1510,1279,1224,581,1242,700,1529,624,1584,1471,202,1211,1726,1255,1855,616,1834,1953,987,1441,798,1542,550,1715,1100,1047,1777,1929,543,735,1688,1683,345,1601,1420,1333,1229,958],[1502,1327,1647,1188,1430,1768,806,1875,565,1024,528,1258,603,490,935,438,301,1751,1161,1276,1606,1665,376,783,1143,1560,1571,663,697,1596,726,1128,313,1410,1020,1444,1935,1816,1346,912],[0.39,0.02,0.19,0.29,0.54,0.03,0.04,0.36,0.47,0.38,0.69,0.65,0.46,0.2,0.26,0.77,0.86,0.59,0.22,0.34,0.63,0.83,0.89,0.42,0.94,0.45,0.95,0.58,0.01,0.28,0.32,0.96,0.07,0.76,0.13,0.05,0.85,0.75,0.31,0.23],[-0.02,0.01,0.28,0.12,0.32,0,-0.5,-0.01,0.27,0.24,-0.11,-0.4,-0.06,0.31,0.15,0.41,0.42,-0.05,-0.16,-0.48,0.18,-0.45,0.05,0.02,0.43,0.04,-0.46,-0.25,-0.14,0.37,0.16,-0.34,-0.32,0.44,0.26,-0.43,-0.13,-0.42,-0.09,-0.2],[0.81597765465267,0.647259329678491,0.120328583521768,0.543800154002383,0.184729989385232,0.635790845612064,0.0742989955469966,0.0419759317301214,0.370317112421617,0.757252902723849,0.00186207285150886,0.159799489425495,0.144741663709283,0.519396774005145,0.609476454323158,0.122510588727891,0.773217808688059,0.514508979162201,0.595448171719909,0.850909892003983,0.842836875235662,0.570326561806723,0.426557252649218,0.137205496430397,0.163092608796433,0.93508125981316,0.537011651322246,0.997654764913023,0.478951843688264,0.773609737167135,0.467988230520859,0.637632509926334,0.256522512063384,0.405364905018359,0.17088253586553,0.0679756663739681,0.846031822729856,0.549878273857757,0.804842539597303,0.765064378036186]],"container":"<table class=\"display\">\n  <thead>\n    <tr>\n      <th> <\/th>\n      <th>type1<\/th>\n      <th>type2<\/th>\n      <th>value<\/th>\n      <th>value1<\/th>\n      <th>value2<\/th>\n      <th>prob1<\/th>\n      <th>prob2<\/th>\n      <th>value3<\/th>\n    <\/tr>\n  <\/thead>\n<\/table>","options":{"pageLength":5,"dom":"ftip","columnDefs":[{"targets":8,"render":"function(data, type, row, meta) {\n    return type !== 'display' ? data : DTWidget.formatSignif(data, 3, 3, \",\", \".\", null);\n  }"},{"className":"dt-right","targets":[3,4,5,6,7,8]},{"orderable":false,"targets":0}],"order":[],"autoWidth":false,"orderClasses":false,"lengthMenu":[5,10,25,50,100]}},"evals":["options.columnDefs.0.render"],"jsHooks":[]}</script>

### 1.6.3.日期格式

-   `formatDate()`：用于转换各类日期格式的函数，可选参数如下。

    -   columns：用于指定转换日期格式的目标列，可以为一列或多列。
    -   method：可选的转换日期格式的方法，见`DT:::DateMethods`，共有”toDateString”、“toISOString”、“toLocaleDateString”、“toLocaleString”、“toLocaleTimeString”、“toString”、“toTimeString”、“toUTCString”等8种方法，设定具体参数时可填入一种或多种。
    -   params：用于指定各类转换后的日期格式中的具体字符。
    -   rows：指定目标列中的目标行。

``` r
date <-
  matrix(rep(c(Sys.time(), Sys.Date()), 8),
         nrow = 2,
         ncol = 8,
         byrow = T)
date <- as.data.frame(date)
methods <- c(
  'toDateString',
  'toISOString',
  'toLocaleDateString',
  'toLocaleString',
  'toLocaleTimeString',
  'toString',
  'toTimeString',
  'toUTCString'
)
colnames(date) <- methods

datatable(
  date * 1000,
  extensions = 'FixedColumns', # 冻结窗格
  options = list(
    dom = 't',
    scrollX = TRUE,
    fixedColumns = list(leftColumns = 2, rightColumns = 1)
  )
) |>
  formatDate(columns = 1:8,
             method = methods)
```

<div id="htmlwidget-37" style="width:100%;height:auto;" class="datatables html-widget"></div>
<script type="application/json" data-for="htmlwidget-37">{"x":{"filter":"none","vertical":false,"extensions":["FixedColumns"],"data":[["1","2"],[1670632282851.04,1670632282851.04],[1670630400000,1670630400000],[1670632282851.04,1670632282851.04],[1670630400000,1670630400000],[1670632282851.04,1670632282851.04],[1670630400000,1670630400000],[1670632282851.04,1670632282851.04],[1670630400000,1670630400000]],"container":"<table class=\"display\">\n  <thead>\n    <tr>\n      <th> <\/th>\n      <th>toDateString<\/th>\n      <th>toISOString<\/th>\n      <th>toLocaleDateString<\/th>\n      <th>toLocaleString<\/th>\n      <th>toLocaleTimeString<\/th>\n      <th>toString<\/th>\n      <th>toTimeString<\/th>\n      <th>toUTCString<\/th>\n    <\/tr>\n  <\/thead>\n<\/table>","options":{"pageLength":5,"dom":"t","scrollX":true,"fixedColumns":{"leftColumns":2,"rightColumns":1},"columnDefs":[{"targets":1,"render":"function(data, type, row, meta) {\n    return type !== 'display' ? data : DTWidget.formatDate(data, \"toDateString\");\n  }"},{"targets":2,"render":"function(data, type, row, meta) {\n    return type !== 'display' ? data : DTWidget.formatDate(data, \"toISOString\");\n  }"},{"targets":3,"render":"function(data, type, row, meta) {\n    return type !== 'display' ? data : DTWidget.formatDate(data, \"toLocaleDateString\");\n  }"},{"targets":4,"render":"function(data, type, row, meta) {\n    return type !== 'display' ? data : DTWidget.formatDate(data, \"toLocaleString\");\n  }"},{"targets":5,"render":"function(data, type, row, meta) {\n    return type !== 'display' ? data : DTWidget.formatDate(data, \"toLocaleTimeString\");\n  }"},{"targets":6,"render":"function(data, type, row, meta) {\n    return type !== 'display' ? data : DTWidget.formatDate(data, \"toString\");\n  }"},{"targets":7,"render":"function(data, type, row, meta) {\n    return type !== 'display' ? data : DTWidget.formatDate(data, \"toTimeString\");\n  }"},{"targets":8,"render":"function(data, type, row, meta) {\n    return type !== 'display' ? data : DTWidget.formatDate(data, \"toUTCString\");\n  }"},{"className":"dt-right","targets":[1,2,3,4,5,6,7,8]},{"orderable":false,"targets":0}],"order":[],"autoWidth":false,"orderClasses":false,"lengthMenu":[5,10,25,50,100]}},"evals":["options.columnDefs.0.render","options.columnDefs.1.render","options.columnDefs.2.render","options.columnDefs.3.render","options.columnDefs.4.render","options.columnDefs.5.render","options.columnDefs.6.render","options.columnDefs.7.render"],"jsHooks":[]}</script>

### 1.6.4.插入超链接

在 html 中的 `<a>` 元素的 [href 属性](https://www.w3school.com.cn/tags/att_a_href.asp)可写入所需指向的超链接地址，对应的 html 代码为`<a class="自定义 css 样式" href="超链接地址" title="超链接title">超链接显示名</a>`。在 DT 包中的实现方法是，针对目标列通过`render = JS()`的方式引入 JS，在此基础上引入 html 和 css。

``` r
# 准备一些超链接所指向的地址
hrefvalue = c(rep("https://yufree.cn/cn/", 2),
              rep("https://xiangyun.rbind.io/post/", 2)) 
hrefdata <- cbind(data, hrefvalue) # hrefvalue 作为第8列

# 由于超链接地址在表中第8列，所以列渲染时写row[8]
datatable(hrefdata,
          options = list(columnDefs = list(
            list(
              targets = 2,
              render = JS(
                "function(data, type, row, meta) {
                  return  '<a href=' + row[8] + '>' + data + '</a>'
                  }"
              )
            ), list(targets = 8, visible = FALSE) # 隐藏 hrefvalue 列
          )))
```

<div id="htmlwidget-38" style="width:100%;height:auto;" class="datatables html-widget"></div>
<script type="application/json" data-for="htmlwidget-38">{"x":{"filter":"none","vertical":false,"data":[["1","2","3","4","5","6","7","8","9","10","11","12","13","14","15","16","17","18","19","20","21","22","23","24","25","26","27","28","29","30","31","32","33","34","35","36","37","38","39","40"],["A","A","B","B","C","C","D","D","E","E","F","F","G","G","H","H","I","I","J","J","K","K","L","L","M","M","N","N","O","O","P","P","Q","Q","R","R","S","S","T","T"],["NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES"],[2227,3458,4870,2707,2773,4750,2475,2122,4280,3293,3271,3521,2950,4159,4517,3988,2512,2799,4496,4425,4716,3547,3998,2827,2427,3989,2358,4197,2987,3130,2275,3597,3607,4499,2796,2193,4631,2492,4303,2233],[1134,1576,1510,1279,1224,581,1242,700,1529,624,1584,1471,202,1211,1726,1255,1855,616,1834,1953,987,1441,798,1542,550,1715,1100,1047,1777,1929,543,735,1688,1683,345,1601,1420,1333,1229,958],[1502,1327,1647,1188,1430,1768,806,1875,565,1024,528,1258,603,490,935,438,301,1751,1161,1276,1606,1665,376,783,1143,1560,1571,663,697,1596,726,1128,313,1410,1020,1444,1935,1816,1346,912],[0.39,0.02,0.19,0.29,0.54,0.03,0.04,0.36,0.47,0.38,0.69,0.65,0.46,0.2,0.26,0.77,0.86,0.59,0.22,0.34,0.63,0.83,0.89,0.42,0.94,0.45,0.95,0.58,0.01,0.28,0.32,0.96,0.07,0.76,0.13,0.05,0.85,0.75,0.31,0.23],[-0.02,0.01,0.28,0.12,0.32,0,-0.5,-0.01,0.27,0.24,-0.11,-0.4,-0.06,0.31,0.15,0.41,0.42,-0.05,-0.16,-0.48,0.18,-0.45,0.05,0.02,0.43,0.04,-0.46,-0.25,-0.14,0.37,0.16,-0.34,-0.32,0.44,0.26,-0.43,-0.13,-0.42,-0.09,-0.2],["https://yufree.cn/cn/","https://yufree.cn/cn/","https://xiangyun.rbind.io/post/","https://xiangyun.rbind.io/post/","https://yufree.cn/cn/","https://yufree.cn/cn/","https://xiangyun.rbind.io/post/","https://xiangyun.rbind.io/post/","https://yufree.cn/cn/","https://yufree.cn/cn/","https://xiangyun.rbind.io/post/","https://xiangyun.rbind.io/post/","https://yufree.cn/cn/","https://yufree.cn/cn/","https://xiangyun.rbind.io/post/","https://xiangyun.rbind.io/post/","https://yufree.cn/cn/","https://yufree.cn/cn/","https://xiangyun.rbind.io/post/","https://xiangyun.rbind.io/post/","https://yufree.cn/cn/","https://yufree.cn/cn/","https://xiangyun.rbind.io/post/","https://xiangyun.rbind.io/post/","https://yufree.cn/cn/","https://yufree.cn/cn/","https://xiangyun.rbind.io/post/","https://xiangyun.rbind.io/post/","https://yufree.cn/cn/","https://yufree.cn/cn/","https://xiangyun.rbind.io/post/","https://xiangyun.rbind.io/post/","https://yufree.cn/cn/","https://yufree.cn/cn/","https://xiangyun.rbind.io/post/","https://xiangyun.rbind.io/post/","https://yufree.cn/cn/","https://yufree.cn/cn/","https://xiangyun.rbind.io/post/","https://xiangyun.rbind.io/post/"]],"container":"<table class=\"display\">\n  <thead>\n    <tr>\n      <th> <\/th>\n      <th>type1<\/th>\n      <th>type2<\/th>\n      <th>value<\/th>\n      <th>value1<\/th>\n      <th>value2<\/th>\n      <th>prob1<\/th>\n      <th>prob2<\/th>\n      <th>hrefvalue<\/th>\n    <\/tr>\n  <\/thead>\n<\/table>","options":{"pageLength":5,"dom":"ftip","columnDefs":[{"targets":2,"render":"function(data, type, row, meta) {\n                  return  '<a href=' + row[8] + '>' + data + '<\/a>'\n                  }"},{"targets":8,"visible":false},{"className":"dt-right","targets":[3,4,5,6,7]},{"orderable":false,"targets":0}],"order":[],"autoWidth":false,"orderClasses":false,"lengthMenu":[5,10,25,50,100]}},"evals":["options.columnDefs.0.render"],"jsHooks":[]}</script>

### 1.6.5.插入图片

在 html 中的[`<img>`元素](https://www.w3school.com.cn/tags/tag_img.asp)可写入所需展示的图像地址，对应的 html 代码为`<img class="自定义 css 样式" src="图片链接" alt="图片alt">`，图片的 alt 属性是指当图像无法正常显示时，页面上展示的替代文本。这里的图片链接可以是指向图片的网页链接，也可以是本地文件中的图片地址。下面的例子中，笔者在项目文件中准备了两张图片，相对地址分别是 `images/USA.png` 和 `images/China.png`。

``` r
imgvalue <- c(rep('China', 2), rep('USA', 2)) # 图片名字
imgdata <- cbind(data, imgvalue)

# 由于图片名字在表中第8列，所以列渲染时写row[8]
datatable(imgdata,
          options = list(columnDefs = list(
            list(
              targets = 1,
              render = JS("function(data, type, row, meta) {
                  return  '<img src=\"images/' + row[8] + '.png\" />' + data
                  }")
            ), list(targets = 8, visible = FALSE) # 隐藏 imgvalue 列
          )))
```

<div id="htmlwidget-39" style="width:100%;height:auto;" class="datatables html-widget"></div>
<script type="application/json" data-for="htmlwidget-39">{"x":{"filter":"none","vertical":false,"data":[["1","2","3","4","5","6","7","8","9","10","11","12","13","14","15","16","17","18","19","20","21","22","23","24","25","26","27","28","29","30","31","32","33","34","35","36","37","38","39","40"],["A","A","B","B","C","C","D","D","E","E","F","F","G","G","H","H","I","I","J","J","K","K","L","L","M","M","N","N","O","O","P","P","Q","Q","R","R","S","S","T","T"],["NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES"],[2227,3458,4870,2707,2773,4750,2475,2122,4280,3293,3271,3521,2950,4159,4517,3988,2512,2799,4496,4425,4716,3547,3998,2827,2427,3989,2358,4197,2987,3130,2275,3597,3607,4499,2796,2193,4631,2492,4303,2233],[1134,1576,1510,1279,1224,581,1242,700,1529,624,1584,1471,202,1211,1726,1255,1855,616,1834,1953,987,1441,798,1542,550,1715,1100,1047,1777,1929,543,735,1688,1683,345,1601,1420,1333,1229,958],[1502,1327,1647,1188,1430,1768,806,1875,565,1024,528,1258,603,490,935,438,301,1751,1161,1276,1606,1665,376,783,1143,1560,1571,663,697,1596,726,1128,313,1410,1020,1444,1935,1816,1346,912],[0.39,0.02,0.19,0.29,0.54,0.03,0.04,0.36,0.47,0.38,0.69,0.65,0.46,0.2,0.26,0.77,0.86,0.59,0.22,0.34,0.63,0.83,0.89,0.42,0.94,0.45,0.95,0.58,0.01,0.28,0.32,0.96,0.07,0.76,0.13,0.05,0.85,0.75,0.31,0.23],[-0.02,0.01,0.28,0.12,0.32,0,-0.5,-0.01,0.27,0.24,-0.11,-0.4,-0.06,0.31,0.15,0.41,0.42,-0.05,-0.16,-0.48,0.18,-0.45,0.05,0.02,0.43,0.04,-0.46,-0.25,-0.14,0.37,0.16,-0.34,-0.32,0.44,0.26,-0.43,-0.13,-0.42,-0.09,-0.2],["China","China","USA","USA","China","China","USA","USA","China","China","USA","USA","China","China","USA","USA","China","China","USA","USA","China","China","USA","USA","China","China","USA","USA","China","China","USA","USA","China","China","USA","USA","China","China","USA","USA"]],"container":"<table class=\"display\">\n  <thead>\n    <tr>\n      <th> <\/th>\n      <th>type1<\/th>\n      <th>type2<\/th>\n      <th>value<\/th>\n      <th>value1<\/th>\n      <th>value2<\/th>\n      <th>prob1<\/th>\n      <th>prob2<\/th>\n      <th>imgvalue<\/th>\n    <\/tr>\n  <\/thead>\n<\/table>","options":{"pageLength":5,"dom":"ftip","columnDefs":[{"targets":1,"render":"function(data, type, row, meta) {\n                  return  '<img src=\"images/' + row[8] + '.png\" />' + data\n                  }"},{"targets":8,"visible":false},{"className":"dt-right","targets":[3,4,5,6,7]},{"orderable":false,"targets":0}],"order":[],"autoWidth":false,"orderClasses":false,"lengthMenu":[5,10,25,50,100]}},"evals":["options.columnDefs.0.render"],"jsHooks":[]}</script>

若不作任何样式设定的话，图片大小和表格中数字、字符的大小相比显得比例失衡，因此也可以在插入图片时引入 css 样式，进行一番调整。

``` css
.team-flag {
  height: 1.3rem;
  border: 1px solid #f0f0f0;
}

.team-name {
  margin-left: 0.5rem;
  font-size: 1.125rem;
  font-weight: 700;
}
```

<style type="text/css">
.team-flag {
  height: 1.3rem;
  border: 1px solid #f0f0f0;
}

.team-name {
  margin-left: 0.5rem;
  font-size: 1.125rem;
  font-weight: 700;
}
</style>

``` r
datatable(imgdata,
          options = list(columnDefs = list(
            list(
              targets = 1,
              render = JS(
                "function(data, type, row, meta) {
return '<img class=\"team-flag\" src=\"images/'+ row[8] + '.png\" />'
         +'<span class=\"team-name\">'+ data +'<span/>' }"
              )
            ),
list(targets = 8, visible = FALSE)
          )))
```

<div id="htmlwidget-40" style="width:100%;height:auto;" class="datatables html-widget"></div>
<script type="application/json" data-for="htmlwidget-40">{"x":{"filter":"none","vertical":false,"data":[["1","2","3","4","5","6","7","8","9","10","11","12","13","14","15","16","17","18","19","20","21","22","23","24","25","26","27","28","29","30","31","32","33","34","35","36","37","38","39","40"],["A","A","B","B","C","C","D","D","E","E","F","F","G","G","H","H","I","I","J","J","K","K","L","L","M","M","N","N","O","O","P","P","Q","Q","R","R","S","S","T","T"],["NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES"],[2227,3458,4870,2707,2773,4750,2475,2122,4280,3293,3271,3521,2950,4159,4517,3988,2512,2799,4496,4425,4716,3547,3998,2827,2427,3989,2358,4197,2987,3130,2275,3597,3607,4499,2796,2193,4631,2492,4303,2233],[1134,1576,1510,1279,1224,581,1242,700,1529,624,1584,1471,202,1211,1726,1255,1855,616,1834,1953,987,1441,798,1542,550,1715,1100,1047,1777,1929,543,735,1688,1683,345,1601,1420,1333,1229,958],[1502,1327,1647,1188,1430,1768,806,1875,565,1024,528,1258,603,490,935,438,301,1751,1161,1276,1606,1665,376,783,1143,1560,1571,663,697,1596,726,1128,313,1410,1020,1444,1935,1816,1346,912],[0.39,0.02,0.19,0.29,0.54,0.03,0.04,0.36,0.47,0.38,0.69,0.65,0.46,0.2,0.26,0.77,0.86,0.59,0.22,0.34,0.63,0.83,0.89,0.42,0.94,0.45,0.95,0.58,0.01,0.28,0.32,0.96,0.07,0.76,0.13,0.05,0.85,0.75,0.31,0.23],[-0.02,0.01,0.28,0.12,0.32,0,-0.5,-0.01,0.27,0.24,-0.11,-0.4,-0.06,0.31,0.15,0.41,0.42,-0.05,-0.16,-0.48,0.18,-0.45,0.05,0.02,0.43,0.04,-0.46,-0.25,-0.14,0.37,0.16,-0.34,-0.32,0.44,0.26,-0.43,-0.13,-0.42,-0.09,-0.2],["China","China","USA","USA","China","China","USA","USA","China","China","USA","USA","China","China","USA","USA","China","China","USA","USA","China","China","USA","USA","China","China","USA","USA","China","China","USA","USA","China","China","USA","USA","China","China","USA","USA"]],"container":"<table class=\"display\">\n  <thead>\n    <tr>\n      <th> <\/th>\n      <th>type1<\/th>\n      <th>type2<\/th>\n      <th>value<\/th>\n      <th>value1<\/th>\n      <th>value2<\/th>\n      <th>prob1<\/th>\n      <th>prob2<\/th>\n      <th>imgvalue<\/th>\n    <\/tr>\n  <\/thead>\n<\/table>","options":{"pageLength":5,"dom":"ftip","columnDefs":[{"targets":1,"render":"function(data, type, row, meta) {\nreturn '<img class=\"team-flag\" src=\"images/'+ row[8] + '.png\" />'\n         +'<span class=\"team-name\">'+ data +'<span/>' }"},{"targets":8,"visible":false},{"className":"dt-right","targets":[3,4,5,6,7]},{"orderable":false,"targets":0}],"order":[],"autoWidth":false,"orderClasses":false,"lengthMenu":[5,10,25,50,100]}},"evals":["options.columnDefs.0.render"],"jsHooks":[]}</script>

### 1.6.6.插入字体图标（fontawesome）

shiny 包中有个 icon 函数，可以方便地从字体图标库 [Font Awesome](https://fontawesome.com/icons) 或 [Bootstrap Glyphicons](https://getbootstrap.com/docs/3.3/components/) 中引入字体图标。而 Font Awesome 库在 R 中也有对应的 R 包 [fontawesome](https://cran.r-project.org/web//packages/fontawesome/fontawesome.pdf)，本小节根据该库举两个简单的例子。

-   插入一个字体图标。

``` r
library(fontawesome)

icon1 <- as.data.table(data)
icon1 <- icon1[, ':='(level = ifelse(
  type2 == "YES",
  fontawesome::fa(name = "thumbs-up"),
  fontawesome::fa(name = "thumbs-down")
))]

datatable(icon1, escape = FALSE)
```

<div id="htmlwidget-41" style="width:100%;height:auto;" class="datatables html-widget"></div>
<script type="application/json" data-for="htmlwidget-41">{"x":{"filter":"none","vertical":false,"data":[["1","2","3","4","5","6","7","8","9","10","11","12","13","14","15","16","17","18","19","20","21","22","23","24","25","26","27","28","29","30","31","32","33","34","35","36","37","38","39","40"],["A","A","B","B","C","C","D","D","E","E","F","F","G","G","H","H","I","I","J","J","K","K","L","L","M","M","N","N","O","O","P","P","Q","Q","R","R","S","S","T","T"],["NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES"],[2227,3458,4870,2707,2773,4750,2475,2122,4280,3293,3271,3521,2950,4159,4517,3988,2512,2799,4496,4425,4716,3547,3998,2827,2427,3989,2358,4197,2987,3130,2275,3597,3607,4499,2796,2193,4631,2492,4303,2233],[1134,1576,1510,1279,1224,581,1242,700,1529,624,1584,1471,202,1211,1726,1255,1855,616,1834,1953,987,1441,798,1542,550,1715,1100,1047,1777,1929,543,735,1688,1683,345,1601,1420,1333,1229,958],[1502,1327,1647,1188,1430,1768,806,1875,565,1024,528,1258,603,490,935,438,301,1751,1161,1276,1606,1665,376,783,1143,1560,1571,663,697,1596,726,1128,313,1410,1020,1444,1935,1816,1346,912],[0.39,0.02,0.19,0.29,0.54,0.03,0.04,0.36,0.47,0.38,0.69,0.65,0.46,0.2,0.26,0.77,0.86,0.59,0.22,0.34,0.63,0.83,0.89,0.42,0.94,0.45,0.95,0.58,0.01,0.28,0.32,0.96,0.07,0.76,0.13,0.05,0.85,0.75,0.31,0.23],[-0.02,0.01,0.28,0.12,0.32,0,-0.5,-0.01,0.27,0.24,-0.11,-0.4,-0.06,0.31,0.15,0.41,0.42,-0.05,-0.16,-0.48,0.18,-0.45,0.05,0.02,0.43,0.04,-0.46,-0.25,-0.14,0.37,0.16,-0.34,-0.32,0.44,0.26,-0.43,-0.13,-0.42,-0.09,-0.2],["<svg aria-hidden=\"true\" role=\"img\" viewBox=\"0 0 512 512\" style=\"height:1em;width:1em;vertical-align:-0.125em;margin-left:auto;margin-right:auto;font-size:inherit;fill:currentColor;overflow:visible;position:relative;\"><path d=\"M128 288V64.03c0-17.67-14.33-31.1-32-31.1H32c-17.67 0-32 14.33-32 31.1v223.1c0 17.67 14.33 31.1 32 31.1h64C113.7 320 128 305.7 128 288zM481.5 229.1c1.234-5.092 1.875-10.32 1.875-15.64c0-22.7-11.44-43.13-29.28-55.28c.4219-3.015 .6406-6.076 .6406-9.122c0-22.32-11.06-42.6-28.83-54.83c-2.438-34.71-31.47-62.2-66.8-62.2h-52.53c-35.94 0-71.55 11.87-100.3 33.41L169.6 92.93c-6.285 4.71-9.596 11.85-9.596 19.13c0 12.76 10.29 24.04 24.03 24.04c5.013 0 10.07-1.565 14.38-4.811l36.66-27.51c20.48-15.34 45.88-23.81 71.5-23.81h52.53c10.45 0 18.97 8.497 18.97 18.95c0 3.5-1.11 4.94-1.11 9.456c0 26.97 29.77 17.91 29.77 40.64c0 9.254-6.392 10.96-6.392 22.25c0 13.97 10.85 21.95 19.58 23.59c8.953 1.671 15.45 9.481 15.45 18.56c0 13.04-11.39 13.37-11.39 28.91c0 12.54 9.702 23.08 22.36 23.94C456.2 266.1 464 275.2 464 284.1c0 10.43-8.516 18.93-18.97 18.93H307.4c-12.44 0-24 10.02-24 23.1c0 4.038 1.02 8.078 3.066 11.72C304.4 371.7 312 403.8 312 411.2c0 8.044-5.984 20.79-22.06 20.79c-12.53 0-14.27-.9059-24.94-28.07c-24.75-62.91-61.74-99.9-80.98-99.9c-13.8 0-24.02 11.27-24.02 23.99c0 7.041 3.083 14.02 9.016 18.76C238.1 402 211.4 480 289.9 480C333.8 480 360 445 360 411.2c0-12.7-5.328-35.21-14.83-59.33h99.86C481.1 351.9 512 321.9 512 284.1C512 261.8 499.9 241 481.5 229.1z\"/><\/svg>","<svg aria-hidden=\"true\" role=\"img\" viewBox=\"0 0 512 512\" style=\"height:1em;width:1em;vertical-align:-0.125em;margin-left:auto;margin-right:auto;font-size:inherit;fill:currentColor;overflow:visible;position:relative;\"><path d=\"M96 191.1H32c-17.67 0-32 14.33-32 31.1v223.1c0 17.67 14.33 31.1 32 31.1h64c17.67 0 32-14.33 32-31.1V223.1C128 206.3 113.7 191.1 96 191.1zM512 227c0-36.89-30.05-66.92-66.97-66.92h-99.86C354.7 135.1 360 113.5 360 100.8c0-33.8-26.2-68.78-70.06-68.78c-46.61 0-59.36 32.44-69.61 58.5c-31.66 80.5-60.33 66.39-60.33 93.47c0 12.84 10.36 23.99 24.02 23.99c5.256 0 10.55-1.721 14.97-5.26c76.76-61.37 57.97-122.7 90.95-122.7c16.08 0 22.06 12.75 22.06 20.79c0 7.404-7.594 39.55-25.55 71.59c-2.046 3.646-3.066 7.686-3.066 11.72c0 13.92 11.43 23.1 24 23.1h137.6C455.5 208.1 464 216.6 464 227c0 9.809-7.766 18.03-17.67 18.71c-12.66 .8593-22.36 11.4-22.36 23.94c0 15.47 11.39 15.95 11.39 28.91c0 25.37-35.03 12.34-35.03 42.15c0 11.22 6.392 13.03 6.392 22.25c0 22.66-29.77 13.76-29.77 40.64c0 4.515 1.11 5.961 1.11 9.456c0 10.45-8.516 18.95-18.97 18.95h-52.53c-25.62 0-51.02-8.466-71.5-23.81l-36.66-27.51c-4.315-3.245-9.37-4.811-14.38-4.811c-13.85 0-24.03 11.38-24.03 24.04c0 7.287 3.312 14.42 9.596 19.13l36.67 27.52C235 468.1 270.6 480 306.6 480h52.53c35.33 0 64.36-27.49 66.8-62.2c17.77-12.23 28.83-32.51 28.83-54.83c0-3.046-.2187-6.107-.6406-9.122c17.84-12.15 29.28-32.58 29.28-55.28c0-5.311-.6406-10.54-1.875-15.64C499.9 270.1 512 250.2 512 227z\"/><\/svg>","<svg aria-hidden=\"true\" role=\"img\" viewBox=\"0 0 512 512\" style=\"height:1em;width:1em;vertical-align:-0.125em;margin-left:auto;margin-right:auto;font-size:inherit;fill:currentColor;overflow:visible;position:relative;\"><path d=\"M128 288V64.03c0-17.67-14.33-31.1-32-31.1H32c-17.67 0-32 14.33-32 31.1v223.1c0 17.67 14.33 31.1 32 31.1h64C113.7 320 128 305.7 128 288zM481.5 229.1c1.234-5.092 1.875-10.32 1.875-15.64c0-22.7-11.44-43.13-29.28-55.28c.4219-3.015 .6406-6.076 .6406-9.122c0-22.32-11.06-42.6-28.83-54.83c-2.438-34.71-31.47-62.2-66.8-62.2h-52.53c-35.94 0-71.55 11.87-100.3 33.41L169.6 92.93c-6.285 4.71-9.596 11.85-9.596 19.13c0 12.76 10.29 24.04 24.03 24.04c5.013 0 10.07-1.565 14.38-4.811l36.66-27.51c20.48-15.34 45.88-23.81 71.5-23.81h52.53c10.45 0 18.97 8.497 18.97 18.95c0 3.5-1.11 4.94-1.11 9.456c0 26.97 29.77 17.91 29.77 40.64c0 9.254-6.392 10.96-6.392 22.25c0 13.97 10.85 21.95 19.58 23.59c8.953 1.671 15.45 9.481 15.45 18.56c0 13.04-11.39 13.37-11.39 28.91c0 12.54 9.702 23.08 22.36 23.94C456.2 266.1 464 275.2 464 284.1c0 10.43-8.516 18.93-18.97 18.93H307.4c-12.44 0-24 10.02-24 23.1c0 4.038 1.02 8.078 3.066 11.72C304.4 371.7 312 403.8 312 411.2c0 8.044-5.984 20.79-22.06 20.79c-12.53 0-14.27-.9059-24.94-28.07c-24.75-62.91-61.74-99.9-80.98-99.9c-13.8 0-24.02 11.27-24.02 23.99c0 7.041 3.083 14.02 9.016 18.76C238.1 402 211.4 480 289.9 480C333.8 480 360 445 360 411.2c0-12.7-5.328-35.21-14.83-59.33h99.86C481.1 351.9 512 321.9 512 284.1C512 261.8 499.9 241 481.5 229.1z\"/><\/svg>","<svg aria-hidden=\"true\" role=\"img\" viewBox=\"0 0 512 512\" style=\"height:1em;width:1em;vertical-align:-0.125em;margin-left:auto;margin-right:auto;font-size:inherit;fill:currentColor;overflow:visible;position:relative;\"><path d=\"M96 191.1H32c-17.67 0-32 14.33-32 31.1v223.1c0 17.67 14.33 31.1 32 31.1h64c17.67 0 32-14.33 32-31.1V223.1C128 206.3 113.7 191.1 96 191.1zM512 227c0-36.89-30.05-66.92-66.97-66.92h-99.86C354.7 135.1 360 113.5 360 100.8c0-33.8-26.2-68.78-70.06-68.78c-46.61 0-59.36 32.44-69.61 58.5c-31.66 80.5-60.33 66.39-60.33 93.47c0 12.84 10.36 23.99 24.02 23.99c5.256 0 10.55-1.721 14.97-5.26c76.76-61.37 57.97-122.7 90.95-122.7c16.08 0 22.06 12.75 22.06 20.79c0 7.404-7.594 39.55-25.55 71.59c-2.046 3.646-3.066 7.686-3.066 11.72c0 13.92 11.43 23.1 24 23.1h137.6C455.5 208.1 464 216.6 464 227c0 9.809-7.766 18.03-17.67 18.71c-12.66 .8593-22.36 11.4-22.36 23.94c0 15.47 11.39 15.95 11.39 28.91c0 25.37-35.03 12.34-35.03 42.15c0 11.22 6.392 13.03 6.392 22.25c0 22.66-29.77 13.76-29.77 40.64c0 4.515 1.11 5.961 1.11 9.456c0 10.45-8.516 18.95-18.97 18.95h-52.53c-25.62 0-51.02-8.466-71.5-23.81l-36.66-27.51c-4.315-3.245-9.37-4.811-14.38-4.811c-13.85 0-24.03 11.38-24.03 24.04c0 7.287 3.312 14.42 9.596 19.13l36.67 27.52C235 468.1 270.6 480 306.6 480h52.53c35.33 0 64.36-27.49 66.8-62.2c17.77-12.23 28.83-32.51 28.83-54.83c0-3.046-.2187-6.107-.6406-9.122c17.84-12.15 29.28-32.58 29.28-55.28c0-5.311-.6406-10.54-1.875-15.64C499.9 270.1 512 250.2 512 227z\"/><\/svg>","<svg aria-hidden=\"true\" role=\"img\" viewBox=\"0 0 512 512\" style=\"height:1em;width:1em;vertical-align:-0.125em;margin-left:auto;margin-right:auto;font-size:inherit;fill:currentColor;overflow:visible;position:relative;\"><path d=\"M128 288V64.03c0-17.67-14.33-31.1-32-31.1H32c-17.67 0-32 14.33-32 31.1v223.1c0 17.67 14.33 31.1 32 31.1h64C113.7 320 128 305.7 128 288zM481.5 229.1c1.234-5.092 1.875-10.32 1.875-15.64c0-22.7-11.44-43.13-29.28-55.28c.4219-3.015 .6406-6.076 .6406-9.122c0-22.32-11.06-42.6-28.83-54.83c-2.438-34.71-31.47-62.2-66.8-62.2h-52.53c-35.94 0-71.55 11.87-100.3 33.41L169.6 92.93c-6.285 4.71-9.596 11.85-9.596 19.13c0 12.76 10.29 24.04 24.03 24.04c5.013 0 10.07-1.565 14.38-4.811l36.66-27.51c20.48-15.34 45.88-23.81 71.5-23.81h52.53c10.45 0 18.97 8.497 18.97 18.95c0 3.5-1.11 4.94-1.11 9.456c0 26.97 29.77 17.91 29.77 40.64c0 9.254-6.392 10.96-6.392 22.25c0 13.97 10.85 21.95 19.58 23.59c8.953 1.671 15.45 9.481 15.45 18.56c0 13.04-11.39 13.37-11.39 28.91c0 12.54 9.702 23.08 22.36 23.94C456.2 266.1 464 275.2 464 284.1c0 10.43-8.516 18.93-18.97 18.93H307.4c-12.44 0-24 10.02-24 23.1c0 4.038 1.02 8.078 3.066 11.72C304.4 371.7 312 403.8 312 411.2c0 8.044-5.984 20.79-22.06 20.79c-12.53 0-14.27-.9059-24.94-28.07c-24.75-62.91-61.74-99.9-80.98-99.9c-13.8 0-24.02 11.27-24.02 23.99c0 7.041 3.083 14.02 9.016 18.76C238.1 402 211.4 480 289.9 480C333.8 480 360 445 360 411.2c0-12.7-5.328-35.21-14.83-59.33h99.86C481.1 351.9 512 321.9 512 284.1C512 261.8 499.9 241 481.5 229.1z\"/><\/svg>","<svg aria-hidden=\"true\" role=\"img\" viewBox=\"0 0 512 512\" style=\"height:1em;width:1em;vertical-align:-0.125em;margin-left:auto;margin-right:auto;font-size:inherit;fill:currentColor;overflow:visible;position:relative;\"><path d=\"M96 191.1H32c-17.67 0-32 14.33-32 31.1v223.1c0 17.67 14.33 31.1 32 31.1h64c17.67 0 32-14.33 32-31.1V223.1C128 206.3 113.7 191.1 96 191.1zM512 227c0-36.89-30.05-66.92-66.97-66.92h-99.86C354.7 135.1 360 113.5 360 100.8c0-33.8-26.2-68.78-70.06-68.78c-46.61 0-59.36 32.44-69.61 58.5c-31.66 80.5-60.33 66.39-60.33 93.47c0 12.84 10.36 23.99 24.02 23.99c5.256 0 10.55-1.721 14.97-5.26c76.76-61.37 57.97-122.7 90.95-122.7c16.08 0 22.06 12.75 22.06 20.79c0 7.404-7.594 39.55-25.55 71.59c-2.046 3.646-3.066 7.686-3.066 11.72c0 13.92 11.43 23.1 24 23.1h137.6C455.5 208.1 464 216.6 464 227c0 9.809-7.766 18.03-17.67 18.71c-12.66 .8593-22.36 11.4-22.36 23.94c0 15.47 11.39 15.95 11.39 28.91c0 25.37-35.03 12.34-35.03 42.15c0 11.22 6.392 13.03 6.392 22.25c0 22.66-29.77 13.76-29.77 40.64c0 4.515 1.11 5.961 1.11 9.456c0 10.45-8.516 18.95-18.97 18.95h-52.53c-25.62 0-51.02-8.466-71.5-23.81l-36.66-27.51c-4.315-3.245-9.37-4.811-14.38-4.811c-13.85 0-24.03 11.38-24.03 24.04c0 7.287 3.312 14.42 9.596 19.13l36.67 27.52C235 468.1 270.6 480 306.6 480h52.53c35.33 0 64.36-27.49 66.8-62.2c17.77-12.23 28.83-32.51 28.83-54.83c0-3.046-.2187-6.107-.6406-9.122c17.84-12.15 29.28-32.58 29.28-55.28c0-5.311-.6406-10.54-1.875-15.64C499.9 270.1 512 250.2 512 227z\"/><\/svg>","<svg aria-hidden=\"true\" role=\"img\" viewBox=\"0 0 512 512\" style=\"height:1em;width:1em;vertical-align:-0.125em;margin-left:auto;margin-right:auto;font-size:inherit;fill:currentColor;overflow:visible;position:relative;\"><path d=\"M128 288V64.03c0-17.67-14.33-31.1-32-31.1H32c-17.67 0-32 14.33-32 31.1v223.1c0 17.67 14.33 31.1 32 31.1h64C113.7 320 128 305.7 128 288zM481.5 229.1c1.234-5.092 1.875-10.32 1.875-15.64c0-22.7-11.44-43.13-29.28-55.28c.4219-3.015 .6406-6.076 .6406-9.122c0-22.32-11.06-42.6-28.83-54.83c-2.438-34.71-31.47-62.2-66.8-62.2h-52.53c-35.94 0-71.55 11.87-100.3 33.41L169.6 92.93c-6.285 4.71-9.596 11.85-9.596 19.13c0 12.76 10.29 24.04 24.03 24.04c5.013 0 10.07-1.565 14.38-4.811l36.66-27.51c20.48-15.34 45.88-23.81 71.5-23.81h52.53c10.45 0 18.97 8.497 18.97 18.95c0 3.5-1.11 4.94-1.11 9.456c0 26.97 29.77 17.91 29.77 40.64c0 9.254-6.392 10.96-6.392 22.25c0 13.97 10.85 21.95 19.58 23.59c8.953 1.671 15.45 9.481 15.45 18.56c0 13.04-11.39 13.37-11.39 28.91c0 12.54 9.702 23.08 22.36 23.94C456.2 266.1 464 275.2 464 284.1c0 10.43-8.516 18.93-18.97 18.93H307.4c-12.44 0-24 10.02-24 23.1c0 4.038 1.02 8.078 3.066 11.72C304.4 371.7 312 403.8 312 411.2c0 8.044-5.984 20.79-22.06 20.79c-12.53 0-14.27-.9059-24.94-28.07c-24.75-62.91-61.74-99.9-80.98-99.9c-13.8 0-24.02 11.27-24.02 23.99c0 7.041 3.083 14.02 9.016 18.76C238.1 402 211.4 480 289.9 480C333.8 480 360 445 360 411.2c0-12.7-5.328-35.21-14.83-59.33h99.86C481.1 351.9 512 321.9 512 284.1C512 261.8 499.9 241 481.5 229.1z\"/><\/svg>","<svg aria-hidden=\"true\" role=\"img\" viewBox=\"0 0 512 512\" style=\"height:1em;width:1em;vertical-align:-0.125em;margin-left:auto;margin-right:auto;font-size:inherit;fill:currentColor;overflow:visible;position:relative;\"><path d=\"M96 191.1H32c-17.67 0-32 14.33-32 31.1v223.1c0 17.67 14.33 31.1 32 31.1h64c17.67 0 32-14.33 32-31.1V223.1C128 206.3 113.7 191.1 96 191.1zM512 227c0-36.89-30.05-66.92-66.97-66.92h-99.86C354.7 135.1 360 113.5 360 100.8c0-33.8-26.2-68.78-70.06-68.78c-46.61 0-59.36 32.44-69.61 58.5c-31.66 80.5-60.33 66.39-60.33 93.47c0 12.84 10.36 23.99 24.02 23.99c5.256 0 10.55-1.721 14.97-5.26c76.76-61.37 57.97-122.7 90.95-122.7c16.08 0 22.06 12.75 22.06 20.79c0 7.404-7.594 39.55-25.55 71.59c-2.046 3.646-3.066 7.686-3.066 11.72c0 13.92 11.43 23.1 24 23.1h137.6C455.5 208.1 464 216.6 464 227c0 9.809-7.766 18.03-17.67 18.71c-12.66 .8593-22.36 11.4-22.36 23.94c0 15.47 11.39 15.95 11.39 28.91c0 25.37-35.03 12.34-35.03 42.15c0 11.22 6.392 13.03 6.392 22.25c0 22.66-29.77 13.76-29.77 40.64c0 4.515 1.11 5.961 1.11 9.456c0 10.45-8.516 18.95-18.97 18.95h-52.53c-25.62 0-51.02-8.466-71.5-23.81l-36.66-27.51c-4.315-3.245-9.37-4.811-14.38-4.811c-13.85 0-24.03 11.38-24.03 24.04c0 7.287 3.312 14.42 9.596 19.13l36.67 27.52C235 468.1 270.6 480 306.6 480h52.53c35.33 0 64.36-27.49 66.8-62.2c17.77-12.23 28.83-32.51 28.83-54.83c0-3.046-.2187-6.107-.6406-9.122c17.84-12.15 29.28-32.58 29.28-55.28c0-5.311-.6406-10.54-1.875-15.64C499.9 270.1 512 250.2 512 227z\"/><\/svg>","<svg aria-hidden=\"true\" role=\"img\" viewBox=\"0 0 512 512\" style=\"height:1em;width:1em;vertical-align:-0.125em;margin-left:auto;margin-right:auto;font-size:inherit;fill:currentColor;overflow:visible;position:relative;\"><path d=\"M128 288V64.03c0-17.67-14.33-31.1-32-31.1H32c-17.67 0-32 14.33-32 31.1v223.1c0 17.67 14.33 31.1 32 31.1h64C113.7 320 128 305.7 128 288zM481.5 229.1c1.234-5.092 1.875-10.32 1.875-15.64c0-22.7-11.44-43.13-29.28-55.28c.4219-3.015 .6406-6.076 .6406-9.122c0-22.32-11.06-42.6-28.83-54.83c-2.438-34.71-31.47-62.2-66.8-62.2h-52.53c-35.94 0-71.55 11.87-100.3 33.41L169.6 92.93c-6.285 4.71-9.596 11.85-9.596 19.13c0 12.76 10.29 24.04 24.03 24.04c5.013 0 10.07-1.565 14.38-4.811l36.66-27.51c20.48-15.34 45.88-23.81 71.5-23.81h52.53c10.45 0 18.97 8.497 18.97 18.95c0 3.5-1.11 4.94-1.11 9.456c0 26.97 29.77 17.91 29.77 40.64c0 9.254-6.392 10.96-6.392 22.25c0 13.97 10.85 21.95 19.58 23.59c8.953 1.671 15.45 9.481 15.45 18.56c0 13.04-11.39 13.37-11.39 28.91c0 12.54 9.702 23.08 22.36 23.94C456.2 266.1 464 275.2 464 284.1c0 10.43-8.516 18.93-18.97 18.93H307.4c-12.44 0-24 10.02-24 23.1c0 4.038 1.02 8.078 3.066 11.72C304.4 371.7 312 403.8 312 411.2c0 8.044-5.984 20.79-22.06 20.79c-12.53 0-14.27-.9059-24.94-28.07c-24.75-62.91-61.74-99.9-80.98-99.9c-13.8 0-24.02 11.27-24.02 23.99c0 7.041 3.083 14.02 9.016 18.76C238.1 402 211.4 480 289.9 480C333.8 480 360 445 360 411.2c0-12.7-5.328-35.21-14.83-59.33h99.86C481.1 351.9 512 321.9 512 284.1C512 261.8 499.9 241 481.5 229.1z\"/><\/svg>","<svg aria-hidden=\"true\" role=\"img\" viewBox=\"0 0 512 512\" style=\"height:1em;width:1em;vertical-align:-0.125em;margin-left:auto;margin-right:auto;font-size:inherit;fill:currentColor;overflow:visible;position:relative;\"><path d=\"M96 191.1H32c-17.67 0-32 14.33-32 31.1v223.1c0 17.67 14.33 31.1 32 31.1h64c17.67 0 32-14.33 32-31.1V223.1C128 206.3 113.7 191.1 96 191.1zM512 227c0-36.89-30.05-66.92-66.97-66.92h-99.86C354.7 135.1 360 113.5 360 100.8c0-33.8-26.2-68.78-70.06-68.78c-46.61 0-59.36 32.44-69.61 58.5c-31.66 80.5-60.33 66.39-60.33 93.47c0 12.84 10.36 23.99 24.02 23.99c5.256 0 10.55-1.721 14.97-5.26c76.76-61.37 57.97-122.7 90.95-122.7c16.08 0 22.06 12.75 22.06 20.79c0 7.404-7.594 39.55-25.55 71.59c-2.046 3.646-3.066 7.686-3.066 11.72c0 13.92 11.43 23.1 24 23.1h137.6C455.5 208.1 464 216.6 464 227c0 9.809-7.766 18.03-17.67 18.71c-12.66 .8593-22.36 11.4-22.36 23.94c0 15.47 11.39 15.95 11.39 28.91c0 25.37-35.03 12.34-35.03 42.15c0 11.22 6.392 13.03 6.392 22.25c0 22.66-29.77 13.76-29.77 40.64c0 4.515 1.11 5.961 1.11 9.456c0 10.45-8.516 18.95-18.97 18.95h-52.53c-25.62 0-51.02-8.466-71.5-23.81l-36.66-27.51c-4.315-3.245-9.37-4.811-14.38-4.811c-13.85 0-24.03 11.38-24.03 24.04c0 7.287 3.312 14.42 9.596 19.13l36.67 27.52C235 468.1 270.6 480 306.6 480h52.53c35.33 0 64.36-27.49 66.8-62.2c17.77-12.23 28.83-32.51 28.83-54.83c0-3.046-.2187-6.107-.6406-9.122c17.84-12.15 29.28-32.58 29.28-55.28c0-5.311-.6406-10.54-1.875-15.64C499.9 270.1 512 250.2 512 227z\"/><\/svg>","<svg aria-hidden=\"true\" role=\"img\" viewBox=\"0 0 512 512\" style=\"height:1em;width:1em;vertical-align:-0.125em;margin-left:auto;margin-right:auto;font-size:inherit;fill:currentColor;overflow:visible;position:relative;\"><path d=\"M128 288V64.03c0-17.67-14.33-31.1-32-31.1H32c-17.67 0-32 14.33-32 31.1v223.1c0 17.67 14.33 31.1 32 31.1h64C113.7 320 128 305.7 128 288zM481.5 229.1c1.234-5.092 1.875-10.32 1.875-15.64c0-22.7-11.44-43.13-29.28-55.28c.4219-3.015 .6406-6.076 .6406-9.122c0-22.32-11.06-42.6-28.83-54.83c-2.438-34.71-31.47-62.2-66.8-62.2h-52.53c-35.94 0-71.55 11.87-100.3 33.41L169.6 92.93c-6.285 4.71-9.596 11.85-9.596 19.13c0 12.76 10.29 24.04 24.03 24.04c5.013 0 10.07-1.565 14.38-4.811l36.66-27.51c20.48-15.34 45.88-23.81 71.5-23.81h52.53c10.45 0 18.97 8.497 18.97 18.95c0 3.5-1.11 4.94-1.11 9.456c0 26.97 29.77 17.91 29.77 40.64c0 9.254-6.392 10.96-6.392 22.25c0 13.97 10.85 21.95 19.58 23.59c8.953 1.671 15.45 9.481 15.45 18.56c0 13.04-11.39 13.37-11.39 28.91c0 12.54 9.702 23.08 22.36 23.94C456.2 266.1 464 275.2 464 284.1c0 10.43-8.516 18.93-18.97 18.93H307.4c-12.44 0-24 10.02-24 23.1c0 4.038 1.02 8.078 3.066 11.72C304.4 371.7 312 403.8 312 411.2c0 8.044-5.984 20.79-22.06 20.79c-12.53 0-14.27-.9059-24.94-28.07c-24.75-62.91-61.74-99.9-80.98-99.9c-13.8 0-24.02 11.27-24.02 23.99c0 7.041 3.083 14.02 9.016 18.76C238.1 402 211.4 480 289.9 480C333.8 480 360 445 360 411.2c0-12.7-5.328-35.21-14.83-59.33h99.86C481.1 351.9 512 321.9 512 284.1C512 261.8 499.9 241 481.5 229.1z\"/><\/svg>","<svg aria-hidden=\"true\" role=\"img\" viewBox=\"0 0 512 512\" style=\"height:1em;width:1em;vertical-align:-0.125em;margin-left:auto;margin-right:auto;font-size:inherit;fill:currentColor;overflow:visible;position:relative;\"><path d=\"M96 191.1H32c-17.67 0-32 14.33-32 31.1v223.1c0 17.67 14.33 31.1 32 31.1h64c17.67 0 32-14.33 32-31.1V223.1C128 206.3 113.7 191.1 96 191.1zM512 227c0-36.89-30.05-66.92-66.97-66.92h-99.86C354.7 135.1 360 113.5 360 100.8c0-33.8-26.2-68.78-70.06-68.78c-46.61 0-59.36 32.44-69.61 58.5c-31.66 80.5-60.33 66.39-60.33 93.47c0 12.84 10.36 23.99 24.02 23.99c5.256 0 10.55-1.721 14.97-5.26c76.76-61.37 57.97-122.7 90.95-122.7c16.08 0 22.06 12.75 22.06 20.79c0 7.404-7.594 39.55-25.55 71.59c-2.046 3.646-3.066 7.686-3.066 11.72c0 13.92 11.43 23.1 24 23.1h137.6C455.5 208.1 464 216.6 464 227c0 9.809-7.766 18.03-17.67 18.71c-12.66 .8593-22.36 11.4-22.36 23.94c0 15.47 11.39 15.95 11.39 28.91c0 25.37-35.03 12.34-35.03 42.15c0 11.22 6.392 13.03 6.392 22.25c0 22.66-29.77 13.76-29.77 40.64c0 4.515 1.11 5.961 1.11 9.456c0 10.45-8.516 18.95-18.97 18.95h-52.53c-25.62 0-51.02-8.466-71.5-23.81l-36.66-27.51c-4.315-3.245-9.37-4.811-14.38-4.811c-13.85 0-24.03 11.38-24.03 24.04c0 7.287 3.312 14.42 9.596 19.13l36.67 27.52C235 468.1 270.6 480 306.6 480h52.53c35.33 0 64.36-27.49 66.8-62.2c17.77-12.23 28.83-32.51 28.83-54.83c0-3.046-.2187-6.107-.6406-9.122c17.84-12.15 29.28-32.58 29.28-55.28c0-5.311-.6406-10.54-1.875-15.64C499.9 270.1 512 250.2 512 227z\"/><\/svg>","<svg aria-hidden=\"true\" role=\"img\" viewBox=\"0 0 512 512\" style=\"height:1em;width:1em;vertical-align:-0.125em;margin-left:auto;margin-right:auto;font-size:inherit;fill:currentColor;overflow:visible;position:relative;\"><path d=\"M128 288V64.03c0-17.67-14.33-31.1-32-31.1H32c-17.67 0-32 14.33-32 31.1v223.1c0 17.67 14.33 31.1 32 31.1h64C113.7 320 128 305.7 128 288zM481.5 229.1c1.234-5.092 1.875-10.32 1.875-15.64c0-22.7-11.44-43.13-29.28-55.28c.4219-3.015 .6406-6.076 .6406-9.122c0-22.32-11.06-42.6-28.83-54.83c-2.438-34.71-31.47-62.2-66.8-62.2h-52.53c-35.94 0-71.55 11.87-100.3 33.41L169.6 92.93c-6.285 4.71-9.596 11.85-9.596 19.13c0 12.76 10.29 24.04 24.03 24.04c5.013 0 10.07-1.565 14.38-4.811l36.66-27.51c20.48-15.34 45.88-23.81 71.5-23.81h52.53c10.45 0 18.97 8.497 18.97 18.95c0 3.5-1.11 4.94-1.11 9.456c0 26.97 29.77 17.91 29.77 40.64c0 9.254-6.392 10.96-6.392 22.25c0 13.97 10.85 21.95 19.58 23.59c8.953 1.671 15.45 9.481 15.45 18.56c0 13.04-11.39 13.37-11.39 28.91c0 12.54 9.702 23.08 22.36 23.94C456.2 266.1 464 275.2 464 284.1c0 10.43-8.516 18.93-18.97 18.93H307.4c-12.44 0-24 10.02-24 23.1c0 4.038 1.02 8.078 3.066 11.72C304.4 371.7 312 403.8 312 411.2c0 8.044-5.984 20.79-22.06 20.79c-12.53 0-14.27-.9059-24.94-28.07c-24.75-62.91-61.74-99.9-80.98-99.9c-13.8 0-24.02 11.27-24.02 23.99c0 7.041 3.083 14.02 9.016 18.76C238.1 402 211.4 480 289.9 480C333.8 480 360 445 360 411.2c0-12.7-5.328-35.21-14.83-59.33h99.86C481.1 351.9 512 321.9 512 284.1C512 261.8 499.9 241 481.5 229.1z\"/><\/svg>","<svg aria-hidden=\"true\" role=\"img\" viewBox=\"0 0 512 512\" style=\"height:1em;width:1em;vertical-align:-0.125em;margin-left:auto;margin-right:auto;font-size:inherit;fill:currentColor;overflow:visible;position:relative;\"><path d=\"M96 191.1H32c-17.67 0-32 14.33-32 31.1v223.1c0 17.67 14.33 31.1 32 31.1h64c17.67 0 32-14.33 32-31.1V223.1C128 206.3 113.7 191.1 96 191.1zM512 227c0-36.89-30.05-66.92-66.97-66.92h-99.86C354.7 135.1 360 113.5 360 100.8c0-33.8-26.2-68.78-70.06-68.78c-46.61 0-59.36 32.44-69.61 58.5c-31.66 80.5-60.33 66.39-60.33 93.47c0 12.84 10.36 23.99 24.02 23.99c5.256 0 10.55-1.721 14.97-5.26c76.76-61.37 57.97-122.7 90.95-122.7c16.08 0 22.06 12.75 22.06 20.79c0 7.404-7.594 39.55-25.55 71.59c-2.046 3.646-3.066 7.686-3.066 11.72c0 13.92 11.43 23.1 24 23.1h137.6C455.5 208.1 464 216.6 464 227c0 9.809-7.766 18.03-17.67 18.71c-12.66 .8593-22.36 11.4-22.36 23.94c0 15.47 11.39 15.95 11.39 28.91c0 25.37-35.03 12.34-35.03 42.15c0 11.22 6.392 13.03 6.392 22.25c0 22.66-29.77 13.76-29.77 40.64c0 4.515 1.11 5.961 1.11 9.456c0 10.45-8.516 18.95-18.97 18.95h-52.53c-25.62 0-51.02-8.466-71.5-23.81l-36.66-27.51c-4.315-3.245-9.37-4.811-14.38-4.811c-13.85 0-24.03 11.38-24.03 24.04c0 7.287 3.312 14.42 9.596 19.13l36.67 27.52C235 468.1 270.6 480 306.6 480h52.53c35.33 0 64.36-27.49 66.8-62.2c17.77-12.23 28.83-32.51 28.83-54.83c0-3.046-.2187-6.107-.6406-9.122c17.84-12.15 29.28-32.58 29.28-55.28c0-5.311-.6406-10.54-1.875-15.64C499.9 270.1 512 250.2 512 227z\"/><\/svg>","<svg aria-hidden=\"true\" role=\"img\" viewBox=\"0 0 512 512\" style=\"height:1em;width:1em;vertical-align:-0.125em;margin-left:auto;margin-right:auto;font-size:inherit;fill:currentColor;overflow:visible;position:relative;\"><path d=\"M128 288V64.03c0-17.67-14.33-31.1-32-31.1H32c-17.67 0-32 14.33-32 31.1v223.1c0 17.67 14.33 31.1 32 31.1h64C113.7 320 128 305.7 128 288zM481.5 229.1c1.234-5.092 1.875-10.32 1.875-15.64c0-22.7-11.44-43.13-29.28-55.28c.4219-3.015 .6406-6.076 .6406-9.122c0-22.32-11.06-42.6-28.83-54.83c-2.438-34.71-31.47-62.2-66.8-62.2h-52.53c-35.94 0-71.55 11.87-100.3 33.41L169.6 92.93c-6.285 4.71-9.596 11.85-9.596 19.13c0 12.76 10.29 24.04 24.03 24.04c5.013 0 10.07-1.565 14.38-4.811l36.66-27.51c20.48-15.34 45.88-23.81 71.5-23.81h52.53c10.45 0 18.97 8.497 18.97 18.95c0 3.5-1.11 4.94-1.11 9.456c0 26.97 29.77 17.91 29.77 40.64c0 9.254-6.392 10.96-6.392 22.25c0 13.97 10.85 21.95 19.58 23.59c8.953 1.671 15.45 9.481 15.45 18.56c0 13.04-11.39 13.37-11.39 28.91c0 12.54 9.702 23.08 22.36 23.94C456.2 266.1 464 275.2 464 284.1c0 10.43-8.516 18.93-18.97 18.93H307.4c-12.44 0-24 10.02-24 23.1c0 4.038 1.02 8.078 3.066 11.72C304.4 371.7 312 403.8 312 411.2c0 8.044-5.984 20.79-22.06 20.79c-12.53 0-14.27-.9059-24.94-28.07c-24.75-62.91-61.74-99.9-80.98-99.9c-13.8 0-24.02 11.27-24.02 23.99c0 7.041 3.083 14.02 9.016 18.76C238.1 402 211.4 480 289.9 480C333.8 480 360 445 360 411.2c0-12.7-5.328-35.21-14.83-59.33h99.86C481.1 351.9 512 321.9 512 284.1C512 261.8 499.9 241 481.5 229.1z\"/><\/svg>","<svg aria-hidden=\"true\" role=\"img\" viewBox=\"0 0 512 512\" style=\"height:1em;width:1em;vertical-align:-0.125em;margin-left:auto;margin-right:auto;font-size:inherit;fill:currentColor;overflow:visible;position:relative;\"><path d=\"M96 191.1H32c-17.67 0-32 14.33-32 31.1v223.1c0 17.67 14.33 31.1 32 31.1h64c17.67 0 32-14.33 32-31.1V223.1C128 206.3 113.7 191.1 96 191.1zM512 227c0-36.89-30.05-66.92-66.97-66.92h-99.86C354.7 135.1 360 113.5 360 100.8c0-33.8-26.2-68.78-70.06-68.78c-46.61 0-59.36 32.44-69.61 58.5c-31.66 80.5-60.33 66.39-60.33 93.47c0 12.84 10.36 23.99 24.02 23.99c5.256 0 10.55-1.721 14.97-5.26c76.76-61.37 57.97-122.7 90.95-122.7c16.08 0 22.06 12.75 22.06 20.79c0 7.404-7.594 39.55-25.55 71.59c-2.046 3.646-3.066 7.686-3.066 11.72c0 13.92 11.43 23.1 24 23.1h137.6C455.5 208.1 464 216.6 464 227c0 9.809-7.766 18.03-17.67 18.71c-12.66 .8593-22.36 11.4-22.36 23.94c0 15.47 11.39 15.95 11.39 28.91c0 25.37-35.03 12.34-35.03 42.15c0 11.22 6.392 13.03 6.392 22.25c0 22.66-29.77 13.76-29.77 40.64c0 4.515 1.11 5.961 1.11 9.456c0 10.45-8.516 18.95-18.97 18.95h-52.53c-25.62 0-51.02-8.466-71.5-23.81l-36.66-27.51c-4.315-3.245-9.37-4.811-14.38-4.811c-13.85 0-24.03 11.38-24.03 24.04c0 7.287 3.312 14.42 9.596 19.13l36.67 27.52C235 468.1 270.6 480 306.6 480h52.53c35.33 0 64.36-27.49 66.8-62.2c17.77-12.23 28.83-32.51 28.83-54.83c0-3.046-.2187-6.107-.6406-9.122c17.84-12.15 29.28-32.58 29.28-55.28c0-5.311-.6406-10.54-1.875-15.64C499.9 270.1 512 250.2 512 227z\"/><\/svg>","<svg aria-hidden=\"true\" role=\"img\" viewBox=\"0 0 512 512\" style=\"height:1em;width:1em;vertical-align:-0.125em;margin-left:auto;margin-right:auto;font-size:inherit;fill:currentColor;overflow:visible;position:relative;\"><path d=\"M128 288V64.03c0-17.67-14.33-31.1-32-31.1H32c-17.67 0-32 14.33-32 31.1v223.1c0 17.67 14.33 31.1 32 31.1h64C113.7 320 128 305.7 128 288zM481.5 229.1c1.234-5.092 1.875-10.32 1.875-15.64c0-22.7-11.44-43.13-29.28-55.28c.4219-3.015 .6406-6.076 .6406-9.122c0-22.32-11.06-42.6-28.83-54.83c-2.438-34.71-31.47-62.2-66.8-62.2h-52.53c-35.94 0-71.55 11.87-100.3 33.41L169.6 92.93c-6.285 4.71-9.596 11.85-9.596 19.13c0 12.76 10.29 24.04 24.03 24.04c5.013 0 10.07-1.565 14.38-4.811l36.66-27.51c20.48-15.34 45.88-23.81 71.5-23.81h52.53c10.45 0 18.97 8.497 18.97 18.95c0 3.5-1.11 4.94-1.11 9.456c0 26.97 29.77 17.91 29.77 40.64c0 9.254-6.392 10.96-6.392 22.25c0 13.97 10.85 21.95 19.58 23.59c8.953 1.671 15.45 9.481 15.45 18.56c0 13.04-11.39 13.37-11.39 28.91c0 12.54 9.702 23.08 22.36 23.94C456.2 266.1 464 275.2 464 284.1c0 10.43-8.516 18.93-18.97 18.93H307.4c-12.44 0-24 10.02-24 23.1c0 4.038 1.02 8.078 3.066 11.72C304.4 371.7 312 403.8 312 411.2c0 8.044-5.984 20.79-22.06 20.79c-12.53 0-14.27-.9059-24.94-28.07c-24.75-62.91-61.74-99.9-80.98-99.9c-13.8 0-24.02 11.27-24.02 23.99c0 7.041 3.083 14.02 9.016 18.76C238.1 402 211.4 480 289.9 480C333.8 480 360 445 360 411.2c0-12.7-5.328-35.21-14.83-59.33h99.86C481.1 351.9 512 321.9 512 284.1C512 261.8 499.9 241 481.5 229.1z\"/><\/svg>","<svg aria-hidden=\"true\" role=\"img\" viewBox=\"0 0 512 512\" style=\"height:1em;width:1em;vertical-align:-0.125em;margin-left:auto;margin-right:auto;font-size:inherit;fill:currentColor;overflow:visible;position:relative;\"><path d=\"M96 191.1H32c-17.67 0-32 14.33-32 31.1v223.1c0 17.67 14.33 31.1 32 31.1h64c17.67 0 32-14.33 32-31.1V223.1C128 206.3 113.7 191.1 96 191.1zM512 227c0-36.89-30.05-66.92-66.97-66.92h-99.86C354.7 135.1 360 113.5 360 100.8c0-33.8-26.2-68.78-70.06-68.78c-46.61 0-59.36 32.44-69.61 58.5c-31.66 80.5-60.33 66.39-60.33 93.47c0 12.84 10.36 23.99 24.02 23.99c5.256 0 10.55-1.721 14.97-5.26c76.76-61.37 57.97-122.7 90.95-122.7c16.08 0 22.06 12.75 22.06 20.79c0 7.404-7.594 39.55-25.55 71.59c-2.046 3.646-3.066 7.686-3.066 11.72c0 13.92 11.43 23.1 24 23.1h137.6C455.5 208.1 464 216.6 464 227c0 9.809-7.766 18.03-17.67 18.71c-12.66 .8593-22.36 11.4-22.36 23.94c0 15.47 11.39 15.95 11.39 28.91c0 25.37-35.03 12.34-35.03 42.15c0 11.22 6.392 13.03 6.392 22.25c0 22.66-29.77 13.76-29.77 40.64c0 4.515 1.11 5.961 1.11 9.456c0 10.45-8.516 18.95-18.97 18.95h-52.53c-25.62 0-51.02-8.466-71.5-23.81l-36.66-27.51c-4.315-3.245-9.37-4.811-14.38-4.811c-13.85 0-24.03 11.38-24.03 24.04c0 7.287 3.312 14.42 9.596 19.13l36.67 27.52C235 468.1 270.6 480 306.6 480h52.53c35.33 0 64.36-27.49 66.8-62.2c17.77-12.23 28.83-32.51 28.83-54.83c0-3.046-.2187-6.107-.6406-9.122c17.84-12.15 29.28-32.58 29.28-55.28c0-5.311-.6406-10.54-1.875-15.64C499.9 270.1 512 250.2 512 227z\"/><\/svg>","<svg aria-hidden=\"true\" role=\"img\" viewBox=\"0 0 512 512\" style=\"height:1em;width:1em;vertical-align:-0.125em;margin-left:auto;margin-right:auto;font-size:inherit;fill:currentColor;overflow:visible;position:relative;\"><path d=\"M128 288V64.03c0-17.67-14.33-31.1-32-31.1H32c-17.67 0-32 14.33-32 31.1v223.1c0 17.67 14.33 31.1 32 31.1h64C113.7 320 128 305.7 128 288zM481.5 229.1c1.234-5.092 1.875-10.32 1.875-15.64c0-22.7-11.44-43.13-29.28-55.28c.4219-3.015 .6406-6.076 .6406-9.122c0-22.32-11.06-42.6-28.83-54.83c-2.438-34.71-31.47-62.2-66.8-62.2h-52.53c-35.94 0-71.55 11.87-100.3 33.41L169.6 92.93c-6.285 4.71-9.596 11.85-9.596 19.13c0 12.76 10.29 24.04 24.03 24.04c5.013 0 10.07-1.565 14.38-4.811l36.66-27.51c20.48-15.34 45.88-23.81 71.5-23.81h52.53c10.45 0 18.97 8.497 18.97 18.95c0 3.5-1.11 4.94-1.11 9.456c0 26.97 29.77 17.91 29.77 40.64c0 9.254-6.392 10.96-6.392 22.25c0 13.97 10.85 21.95 19.58 23.59c8.953 1.671 15.45 9.481 15.45 18.56c0 13.04-11.39 13.37-11.39 28.91c0 12.54 9.702 23.08 22.36 23.94C456.2 266.1 464 275.2 464 284.1c0 10.43-8.516 18.93-18.97 18.93H307.4c-12.44 0-24 10.02-24 23.1c0 4.038 1.02 8.078 3.066 11.72C304.4 371.7 312 403.8 312 411.2c0 8.044-5.984 20.79-22.06 20.79c-12.53 0-14.27-.9059-24.94-28.07c-24.75-62.91-61.74-99.9-80.98-99.9c-13.8 0-24.02 11.27-24.02 23.99c0 7.041 3.083 14.02 9.016 18.76C238.1 402 211.4 480 289.9 480C333.8 480 360 445 360 411.2c0-12.7-5.328-35.21-14.83-59.33h99.86C481.1 351.9 512 321.9 512 284.1C512 261.8 499.9 241 481.5 229.1z\"/><\/svg>","<svg aria-hidden=\"true\" role=\"img\" viewBox=\"0 0 512 512\" style=\"height:1em;width:1em;vertical-align:-0.125em;margin-left:auto;margin-right:auto;font-size:inherit;fill:currentColor;overflow:visible;position:relative;\"><path d=\"M96 191.1H32c-17.67 0-32 14.33-32 31.1v223.1c0 17.67 14.33 31.1 32 31.1h64c17.67 0 32-14.33 32-31.1V223.1C128 206.3 113.7 191.1 96 191.1zM512 227c0-36.89-30.05-66.92-66.97-66.92h-99.86C354.7 135.1 360 113.5 360 100.8c0-33.8-26.2-68.78-70.06-68.78c-46.61 0-59.36 32.44-69.61 58.5c-31.66 80.5-60.33 66.39-60.33 93.47c0 12.84 10.36 23.99 24.02 23.99c5.256 0 10.55-1.721 14.97-5.26c76.76-61.37 57.97-122.7 90.95-122.7c16.08 0 22.06 12.75 22.06 20.79c0 7.404-7.594 39.55-25.55 71.59c-2.046 3.646-3.066 7.686-3.066 11.72c0 13.92 11.43 23.1 24 23.1h137.6C455.5 208.1 464 216.6 464 227c0 9.809-7.766 18.03-17.67 18.71c-12.66 .8593-22.36 11.4-22.36 23.94c0 15.47 11.39 15.95 11.39 28.91c0 25.37-35.03 12.34-35.03 42.15c0 11.22 6.392 13.03 6.392 22.25c0 22.66-29.77 13.76-29.77 40.64c0 4.515 1.11 5.961 1.11 9.456c0 10.45-8.516 18.95-18.97 18.95h-52.53c-25.62 0-51.02-8.466-71.5-23.81l-36.66-27.51c-4.315-3.245-9.37-4.811-14.38-4.811c-13.85 0-24.03 11.38-24.03 24.04c0 7.287 3.312 14.42 9.596 19.13l36.67 27.52C235 468.1 270.6 480 306.6 480h52.53c35.33 0 64.36-27.49 66.8-62.2c17.77-12.23 28.83-32.51 28.83-54.83c0-3.046-.2187-6.107-.6406-9.122c17.84-12.15 29.28-32.58 29.28-55.28c0-5.311-.6406-10.54-1.875-15.64C499.9 270.1 512 250.2 512 227z\"/><\/svg>","<svg aria-hidden=\"true\" role=\"img\" viewBox=\"0 0 512 512\" style=\"height:1em;width:1em;vertical-align:-0.125em;margin-left:auto;margin-right:auto;font-size:inherit;fill:currentColor;overflow:visible;position:relative;\"><path d=\"M128 288V64.03c0-17.67-14.33-31.1-32-31.1H32c-17.67 0-32 14.33-32 31.1v223.1c0 17.67 14.33 31.1 32 31.1h64C113.7 320 128 305.7 128 288zM481.5 229.1c1.234-5.092 1.875-10.32 1.875-15.64c0-22.7-11.44-43.13-29.28-55.28c.4219-3.015 .6406-6.076 .6406-9.122c0-22.32-11.06-42.6-28.83-54.83c-2.438-34.71-31.47-62.2-66.8-62.2h-52.53c-35.94 0-71.55 11.87-100.3 33.41L169.6 92.93c-6.285 4.71-9.596 11.85-9.596 19.13c0 12.76 10.29 24.04 24.03 24.04c5.013 0 10.07-1.565 14.38-4.811l36.66-27.51c20.48-15.34 45.88-23.81 71.5-23.81h52.53c10.45 0 18.97 8.497 18.97 18.95c0 3.5-1.11 4.94-1.11 9.456c0 26.97 29.77 17.91 29.77 40.64c0 9.254-6.392 10.96-6.392 22.25c0 13.97 10.85 21.95 19.58 23.59c8.953 1.671 15.45 9.481 15.45 18.56c0 13.04-11.39 13.37-11.39 28.91c0 12.54 9.702 23.08 22.36 23.94C456.2 266.1 464 275.2 464 284.1c0 10.43-8.516 18.93-18.97 18.93H307.4c-12.44 0-24 10.02-24 23.1c0 4.038 1.02 8.078 3.066 11.72C304.4 371.7 312 403.8 312 411.2c0 8.044-5.984 20.79-22.06 20.79c-12.53 0-14.27-.9059-24.94-28.07c-24.75-62.91-61.74-99.9-80.98-99.9c-13.8 0-24.02 11.27-24.02 23.99c0 7.041 3.083 14.02 9.016 18.76C238.1 402 211.4 480 289.9 480C333.8 480 360 445 360 411.2c0-12.7-5.328-35.21-14.83-59.33h99.86C481.1 351.9 512 321.9 512 284.1C512 261.8 499.9 241 481.5 229.1z\"/><\/svg>","<svg aria-hidden=\"true\" role=\"img\" viewBox=\"0 0 512 512\" style=\"height:1em;width:1em;vertical-align:-0.125em;margin-left:auto;margin-right:auto;font-size:inherit;fill:currentColor;overflow:visible;position:relative;\"><path d=\"M96 191.1H32c-17.67 0-32 14.33-32 31.1v223.1c0 17.67 14.33 31.1 32 31.1h64c17.67 0 32-14.33 32-31.1V223.1C128 206.3 113.7 191.1 96 191.1zM512 227c0-36.89-30.05-66.92-66.97-66.92h-99.86C354.7 135.1 360 113.5 360 100.8c0-33.8-26.2-68.78-70.06-68.78c-46.61 0-59.36 32.44-69.61 58.5c-31.66 80.5-60.33 66.39-60.33 93.47c0 12.84 10.36 23.99 24.02 23.99c5.256 0 10.55-1.721 14.97-5.26c76.76-61.37 57.97-122.7 90.95-122.7c16.08 0 22.06 12.75 22.06 20.79c0 7.404-7.594 39.55-25.55 71.59c-2.046 3.646-3.066 7.686-3.066 11.72c0 13.92 11.43 23.1 24 23.1h137.6C455.5 208.1 464 216.6 464 227c0 9.809-7.766 18.03-17.67 18.71c-12.66 .8593-22.36 11.4-22.36 23.94c0 15.47 11.39 15.95 11.39 28.91c0 25.37-35.03 12.34-35.03 42.15c0 11.22 6.392 13.03 6.392 22.25c0 22.66-29.77 13.76-29.77 40.64c0 4.515 1.11 5.961 1.11 9.456c0 10.45-8.516 18.95-18.97 18.95h-52.53c-25.62 0-51.02-8.466-71.5-23.81l-36.66-27.51c-4.315-3.245-9.37-4.811-14.38-4.811c-13.85 0-24.03 11.38-24.03 24.04c0 7.287 3.312 14.42 9.596 19.13l36.67 27.52C235 468.1 270.6 480 306.6 480h52.53c35.33 0 64.36-27.49 66.8-62.2c17.77-12.23 28.83-32.51 28.83-54.83c0-3.046-.2187-6.107-.6406-9.122c17.84-12.15 29.28-32.58 29.28-55.28c0-5.311-.6406-10.54-1.875-15.64C499.9 270.1 512 250.2 512 227z\"/><\/svg>","<svg aria-hidden=\"true\" role=\"img\" viewBox=\"0 0 512 512\" style=\"height:1em;width:1em;vertical-align:-0.125em;margin-left:auto;margin-right:auto;font-size:inherit;fill:currentColor;overflow:visible;position:relative;\"><path d=\"M128 288V64.03c0-17.67-14.33-31.1-32-31.1H32c-17.67 0-32 14.33-32 31.1v223.1c0 17.67 14.33 31.1 32 31.1h64C113.7 320 128 305.7 128 288zM481.5 229.1c1.234-5.092 1.875-10.32 1.875-15.64c0-22.7-11.44-43.13-29.28-55.28c.4219-3.015 .6406-6.076 .6406-9.122c0-22.32-11.06-42.6-28.83-54.83c-2.438-34.71-31.47-62.2-66.8-62.2h-52.53c-35.94 0-71.55 11.87-100.3 33.41L169.6 92.93c-6.285 4.71-9.596 11.85-9.596 19.13c0 12.76 10.29 24.04 24.03 24.04c5.013 0 10.07-1.565 14.38-4.811l36.66-27.51c20.48-15.34 45.88-23.81 71.5-23.81h52.53c10.45 0 18.97 8.497 18.97 18.95c0 3.5-1.11 4.94-1.11 9.456c0 26.97 29.77 17.91 29.77 40.64c0 9.254-6.392 10.96-6.392 22.25c0 13.97 10.85 21.95 19.58 23.59c8.953 1.671 15.45 9.481 15.45 18.56c0 13.04-11.39 13.37-11.39 28.91c0 12.54 9.702 23.08 22.36 23.94C456.2 266.1 464 275.2 464 284.1c0 10.43-8.516 18.93-18.97 18.93H307.4c-12.44 0-24 10.02-24 23.1c0 4.038 1.02 8.078 3.066 11.72C304.4 371.7 312 403.8 312 411.2c0 8.044-5.984 20.79-22.06 20.79c-12.53 0-14.27-.9059-24.94-28.07c-24.75-62.91-61.74-99.9-80.98-99.9c-13.8 0-24.02 11.27-24.02 23.99c0 7.041 3.083 14.02 9.016 18.76C238.1 402 211.4 480 289.9 480C333.8 480 360 445 360 411.2c0-12.7-5.328-35.21-14.83-59.33h99.86C481.1 351.9 512 321.9 512 284.1C512 261.8 499.9 241 481.5 229.1z\"/><\/svg>","<svg aria-hidden=\"true\" role=\"img\" viewBox=\"0 0 512 512\" style=\"height:1em;width:1em;vertical-align:-0.125em;margin-left:auto;margin-right:auto;font-size:inherit;fill:currentColor;overflow:visible;position:relative;\"><path d=\"M96 191.1H32c-17.67 0-32 14.33-32 31.1v223.1c0 17.67 14.33 31.1 32 31.1h64c17.67 0 32-14.33 32-31.1V223.1C128 206.3 113.7 191.1 96 191.1zM512 227c0-36.89-30.05-66.92-66.97-66.92h-99.86C354.7 135.1 360 113.5 360 100.8c0-33.8-26.2-68.78-70.06-68.78c-46.61 0-59.36 32.44-69.61 58.5c-31.66 80.5-60.33 66.39-60.33 93.47c0 12.84 10.36 23.99 24.02 23.99c5.256 0 10.55-1.721 14.97-5.26c76.76-61.37 57.97-122.7 90.95-122.7c16.08 0 22.06 12.75 22.06 20.79c0 7.404-7.594 39.55-25.55 71.59c-2.046 3.646-3.066 7.686-3.066 11.72c0 13.92 11.43 23.1 24 23.1h137.6C455.5 208.1 464 216.6 464 227c0 9.809-7.766 18.03-17.67 18.71c-12.66 .8593-22.36 11.4-22.36 23.94c0 15.47 11.39 15.95 11.39 28.91c0 25.37-35.03 12.34-35.03 42.15c0 11.22 6.392 13.03 6.392 22.25c0 22.66-29.77 13.76-29.77 40.64c0 4.515 1.11 5.961 1.11 9.456c0 10.45-8.516 18.95-18.97 18.95h-52.53c-25.62 0-51.02-8.466-71.5-23.81l-36.66-27.51c-4.315-3.245-9.37-4.811-14.38-4.811c-13.85 0-24.03 11.38-24.03 24.04c0 7.287 3.312 14.42 9.596 19.13l36.67 27.52C235 468.1 270.6 480 306.6 480h52.53c35.33 0 64.36-27.49 66.8-62.2c17.77-12.23 28.83-32.51 28.83-54.83c0-3.046-.2187-6.107-.6406-9.122c17.84-12.15 29.28-32.58 29.28-55.28c0-5.311-.6406-10.54-1.875-15.64C499.9 270.1 512 250.2 512 227z\"/><\/svg>","<svg aria-hidden=\"true\" role=\"img\" viewBox=\"0 0 512 512\" style=\"height:1em;width:1em;vertical-align:-0.125em;margin-left:auto;margin-right:auto;font-size:inherit;fill:currentColor;overflow:visible;position:relative;\"><path d=\"M128 288V64.03c0-17.67-14.33-31.1-32-31.1H32c-17.67 0-32 14.33-32 31.1v223.1c0 17.67 14.33 31.1 32 31.1h64C113.7 320 128 305.7 128 288zM481.5 229.1c1.234-5.092 1.875-10.32 1.875-15.64c0-22.7-11.44-43.13-29.28-55.28c.4219-3.015 .6406-6.076 .6406-9.122c0-22.32-11.06-42.6-28.83-54.83c-2.438-34.71-31.47-62.2-66.8-62.2h-52.53c-35.94 0-71.55 11.87-100.3 33.41L169.6 92.93c-6.285 4.71-9.596 11.85-9.596 19.13c0 12.76 10.29 24.04 24.03 24.04c5.013 0 10.07-1.565 14.38-4.811l36.66-27.51c20.48-15.34 45.88-23.81 71.5-23.81h52.53c10.45 0 18.97 8.497 18.97 18.95c0 3.5-1.11 4.94-1.11 9.456c0 26.97 29.77 17.91 29.77 40.64c0 9.254-6.392 10.96-6.392 22.25c0 13.97 10.85 21.95 19.58 23.59c8.953 1.671 15.45 9.481 15.45 18.56c0 13.04-11.39 13.37-11.39 28.91c0 12.54 9.702 23.08 22.36 23.94C456.2 266.1 464 275.2 464 284.1c0 10.43-8.516 18.93-18.97 18.93H307.4c-12.44 0-24 10.02-24 23.1c0 4.038 1.02 8.078 3.066 11.72C304.4 371.7 312 403.8 312 411.2c0 8.044-5.984 20.79-22.06 20.79c-12.53 0-14.27-.9059-24.94-28.07c-24.75-62.91-61.74-99.9-80.98-99.9c-13.8 0-24.02 11.27-24.02 23.99c0 7.041 3.083 14.02 9.016 18.76C238.1 402 211.4 480 289.9 480C333.8 480 360 445 360 411.2c0-12.7-5.328-35.21-14.83-59.33h99.86C481.1 351.9 512 321.9 512 284.1C512 261.8 499.9 241 481.5 229.1z\"/><\/svg>","<svg aria-hidden=\"true\" role=\"img\" viewBox=\"0 0 512 512\" style=\"height:1em;width:1em;vertical-align:-0.125em;margin-left:auto;margin-right:auto;font-size:inherit;fill:currentColor;overflow:visible;position:relative;\"><path d=\"M96 191.1H32c-17.67 0-32 14.33-32 31.1v223.1c0 17.67 14.33 31.1 32 31.1h64c17.67 0 32-14.33 32-31.1V223.1C128 206.3 113.7 191.1 96 191.1zM512 227c0-36.89-30.05-66.92-66.97-66.92h-99.86C354.7 135.1 360 113.5 360 100.8c0-33.8-26.2-68.78-70.06-68.78c-46.61 0-59.36 32.44-69.61 58.5c-31.66 80.5-60.33 66.39-60.33 93.47c0 12.84 10.36 23.99 24.02 23.99c5.256 0 10.55-1.721 14.97-5.26c76.76-61.37 57.97-122.7 90.95-122.7c16.08 0 22.06 12.75 22.06 20.79c0 7.404-7.594 39.55-25.55 71.59c-2.046 3.646-3.066 7.686-3.066 11.72c0 13.92 11.43 23.1 24 23.1h137.6C455.5 208.1 464 216.6 464 227c0 9.809-7.766 18.03-17.67 18.71c-12.66 .8593-22.36 11.4-22.36 23.94c0 15.47 11.39 15.95 11.39 28.91c0 25.37-35.03 12.34-35.03 42.15c0 11.22 6.392 13.03 6.392 22.25c0 22.66-29.77 13.76-29.77 40.64c0 4.515 1.11 5.961 1.11 9.456c0 10.45-8.516 18.95-18.97 18.95h-52.53c-25.62 0-51.02-8.466-71.5-23.81l-36.66-27.51c-4.315-3.245-9.37-4.811-14.38-4.811c-13.85 0-24.03 11.38-24.03 24.04c0 7.287 3.312 14.42 9.596 19.13l36.67 27.52C235 468.1 270.6 480 306.6 480h52.53c35.33 0 64.36-27.49 66.8-62.2c17.77-12.23 28.83-32.51 28.83-54.83c0-3.046-.2187-6.107-.6406-9.122c17.84-12.15 29.28-32.58 29.28-55.28c0-5.311-.6406-10.54-1.875-15.64C499.9 270.1 512 250.2 512 227z\"/><\/svg>","<svg aria-hidden=\"true\" role=\"img\" viewBox=\"0 0 512 512\" style=\"height:1em;width:1em;vertical-align:-0.125em;margin-left:auto;margin-right:auto;font-size:inherit;fill:currentColor;overflow:visible;position:relative;\"><path d=\"M128 288V64.03c0-17.67-14.33-31.1-32-31.1H32c-17.67 0-32 14.33-32 31.1v223.1c0 17.67 14.33 31.1 32 31.1h64C113.7 320 128 305.7 128 288zM481.5 229.1c1.234-5.092 1.875-10.32 1.875-15.64c0-22.7-11.44-43.13-29.28-55.28c.4219-3.015 .6406-6.076 .6406-9.122c0-22.32-11.06-42.6-28.83-54.83c-2.438-34.71-31.47-62.2-66.8-62.2h-52.53c-35.94 0-71.55 11.87-100.3 33.41L169.6 92.93c-6.285 4.71-9.596 11.85-9.596 19.13c0 12.76 10.29 24.04 24.03 24.04c5.013 0 10.07-1.565 14.38-4.811l36.66-27.51c20.48-15.34 45.88-23.81 71.5-23.81h52.53c10.45 0 18.97 8.497 18.97 18.95c0 3.5-1.11 4.94-1.11 9.456c0 26.97 29.77 17.91 29.77 40.64c0 9.254-6.392 10.96-6.392 22.25c0 13.97 10.85 21.95 19.58 23.59c8.953 1.671 15.45 9.481 15.45 18.56c0 13.04-11.39 13.37-11.39 28.91c0 12.54 9.702 23.08 22.36 23.94C456.2 266.1 464 275.2 464 284.1c0 10.43-8.516 18.93-18.97 18.93H307.4c-12.44 0-24 10.02-24 23.1c0 4.038 1.02 8.078 3.066 11.72C304.4 371.7 312 403.8 312 411.2c0 8.044-5.984 20.79-22.06 20.79c-12.53 0-14.27-.9059-24.94-28.07c-24.75-62.91-61.74-99.9-80.98-99.9c-13.8 0-24.02 11.27-24.02 23.99c0 7.041 3.083 14.02 9.016 18.76C238.1 402 211.4 480 289.9 480C333.8 480 360 445 360 411.2c0-12.7-5.328-35.21-14.83-59.33h99.86C481.1 351.9 512 321.9 512 284.1C512 261.8 499.9 241 481.5 229.1z\"/><\/svg>","<svg aria-hidden=\"true\" role=\"img\" viewBox=\"0 0 512 512\" style=\"height:1em;width:1em;vertical-align:-0.125em;margin-left:auto;margin-right:auto;font-size:inherit;fill:currentColor;overflow:visible;position:relative;\"><path d=\"M96 191.1H32c-17.67 0-32 14.33-32 31.1v223.1c0 17.67 14.33 31.1 32 31.1h64c17.67 0 32-14.33 32-31.1V223.1C128 206.3 113.7 191.1 96 191.1zM512 227c0-36.89-30.05-66.92-66.97-66.92h-99.86C354.7 135.1 360 113.5 360 100.8c0-33.8-26.2-68.78-70.06-68.78c-46.61 0-59.36 32.44-69.61 58.5c-31.66 80.5-60.33 66.39-60.33 93.47c0 12.84 10.36 23.99 24.02 23.99c5.256 0 10.55-1.721 14.97-5.26c76.76-61.37 57.97-122.7 90.95-122.7c16.08 0 22.06 12.75 22.06 20.79c0 7.404-7.594 39.55-25.55 71.59c-2.046 3.646-3.066 7.686-3.066 11.72c0 13.92 11.43 23.1 24 23.1h137.6C455.5 208.1 464 216.6 464 227c0 9.809-7.766 18.03-17.67 18.71c-12.66 .8593-22.36 11.4-22.36 23.94c0 15.47 11.39 15.95 11.39 28.91c0 25.37-35.03 12.34-35.03 42.15c0 11.22 6.392 13.03 6.392 22.25c0 22.66-29.77 13.76-29.77 40.64c0 4.515 1.11 5.961 1.11 9.456c0 10.45-8.516 18.95-18.97 18.95h-52.53c-25.62 0-51.02-8.466-71.5-23.81l-36.66-27.51c-4.315-3.245-9.37-4.811-14.38-4.811c-13.85 0-24.03 11.38-24.03 24.04c0 7.287 3.312 14.42 9.596 19.13l36.67 27.52C235 468.1 270.6 480 306.6 480h52.53c35.33 0 64.36-27.49 66.8-62.2c17.77-12.23 28.83-32.51 28.83-54.83c0-3.046-.2187-6.107-.6406-9.122c17.84-12.15 29.28-32.58 29.28-55.28c0-5.311-.6406-10.54-1.875-15.64C499.9 270.1 512 250.2 512 227z\"/><\/svg>","<svg aria-hidden=\"true\" role=\"img\" viewBox=\"0 0 512 512\" style=\"height:1em;width:1em;vertical-align:-0.125em;margin-left:auto;margin-right:auto;font-size:inherit;fill:currentColor;overflow:visible;position:relative;\"><path d=\"M128 288V64.03c0-17.67-14.33-31.1-32-31.1H32c-17.67 0-32 14.33-32 31.1v223.1c0 17.67 14.33 31.1 32 31.1h64C113.7 320 128 305.7 128 288zM481.5 229.1c1.234-5.092 1.875-10.32 1.875-15.64c0-22.7-11.44-43.13-29.28-55.28c.4219-3.015 .6406-6.076 .6406-9.122c0-22.32-11.06-42.6-28.83-54.83c-2.438-34.71-31.47-62.2-66.8-62.2h-52.53c-35.94 0-71.55 11.87-100.3 33.41L169.6 92.93c-6.285 4.71-9.596 11.85-9.596 19.13c0 12.76 10.29 24.04 24.03 24.04c5.013 0 10.07-1.565 14.38-4.811l36.66-27.51c20.48-15.34 45.88-23.81 71.5-23.81h52.53c10.45 0 18.97 8.497 18.97 18.95c0 3.5-1.11 4.94-1.11 9.456c0 26.97 29.77 17.91 29.77 40.64c0 9.254-6.392 10.96-6.392 22.25c0 13.97 10.85 21.95 19.58 23.59c8.953 1.671 15.45 9.481 15.45 18.56c0 13.04-11.39 13.37-11.39 28.91c0 12.54 9.702 23.08 22.36 23.94C456.2 266.1 464 275.2 464 284.1c0 10.43-8.516 18.93-18.97 18.93H307.4c-12.44 0-24 10.02-24 23.1c0 4.038 1.02 8.078 3.066 11.72C304.4 371.7 312 403.8 312 411.2c0 8.044-5.984 20.79-22.06 20.79c-12.53 0-14.27-.9059-24.94-28.07c-24.75-62.91-61.74-99.9-80.98-99.9c-13.8 0-24.02 11.27-24.02 23.99c0 7.041 3.083 14.02 9.016 18.76C238.1 402 211.4 480 289.9 480C333.8 480 360 445 360 411.2c0-12.7-5.328-35.21-14.83-59.33h99.86C481.1 351.9 512 321.9 512 284.1C512 261.8 499.9 241 481.5 229.1z\"/><\/svg>","<svg aria-hidden=\"true\" role=\"img\" viewBox=\"0 0 512 512\" style=\"height:1em;width:1em;vertical-align:-0.125em;margin-left:auto;margin-right:auto;font-size:inherit;fill:currentColor;overflow:visible;position:relative;\"><path d=\"M96 191.1H32c-17.67 0-32 14.33-32 31.1v223.1c0 17.67 14.33 31.1 32 31.1h64c17.67 0 32-14.33 32-31.1V223.1C128 206.3 113.7 191.1 96 191.1zM512 227c0-36.89-30.05-66.92-66.97-66.92h-99.86C354.7 135.1 360 113.5 360 100.8c0-33.8-26.2-68.78-70.06-68.78c-46.61 0-59.36 32.44-69.61 58.5c-31.66 80.5-60.33 66.39-60.33 93.47c0 12.84 10.36 23.99 24.02 23.99c5.256 0 10.55-1.721 14.97-5.26c76.76-61.37 57.97-122.7 90.95-122.7c16.08 0 22.06 12.75 22.06 20.79c0 7.404-7.594 39.55-25.55 71.59c-2.046 3.646-3.066 7.686-3.066 11.72c0 13.92 11.43 23.1 24 23.1h137.6C455.5 208.1 464 216.6 464 227c0 9.809-7.766 18.03-17.67 18.71c-12.66 .8593-22.36 11.4-22.36 23.94c0 15.47 11.39 15.95 11.39 28.91c0 25.37-35.03 12.34-35.03 42.15c0 11.22 6.392 13.03 6.392 22.25c0 22.66-29.77 13.76-29.77 40.64c0 4.515 1.11 5.961 1.11 9.456c0 10.45-8.516 18.95-18.97 18.95h-52.53c-25.62 0-51.02-8.466-71.5-23.81l-36.66-27.51c-4.315-3.245-9.37-4.811-14.38-4.811c-13.85 0-24.03 11.38-24.03 24.04c0 7.287 3.312 14.42 9.596 19.13l36.67 27.52C235 468.1 270.6 480 306.6 480h52.53c35.33 0 64.36-27.49 66.8-62.2c17.77-12.23 28.83-32.51 28.83-54.83c0-3.046-.2187-6.107-.6406-9.122c17.84-12.15 29.28-32.58 29.28-55.28c0-5.311-.6406-10.54-1.875-15.64C499.9 270.1 512 250.2 512 227z\"/><\/svg>","<svg aria-hidden=\"true\" role=\"img\" viewBox=\"0 0 512 512\" style=\"height:1em;width:1em;vertical-align:-0.125em;margin-left:auto;margin-right:auto;font-size:inherit;fill:currentColor;overflow:visible;position:relative;\"><path d=\"M128 288V64.03c0-17.67-14.33-31.1-32-31.1H32c-17.67 0-32 14.33-32 31.1v223.1c0 17.67 14.33 31.1 32 31.1h64C113.7 320 128 305.7 128 288zM481.5 229.1c1.234-5.092 1.875-10.32 1.875-15.64c0-22.7-11.44-43.13-29.28-55.28c.4219-3.015 .6406-6.076 .6406-9.122c0-22.32-11.06-42.6-28.83-54.83c-2.438-34.71-31.47-62.2-66.8-62.2h-52.53c-35.94 0-71.55 11.87-100.3 33.41L169.6 92.93c-6.285 4.71-9.596 11.85-9.596 19.13c0 12.76 10.29 24.04 24.03 24.04c5.013 0 10.07-1.565 14.38-4.811l36.66-27.51c20.48-15.34 45.88-23.81 71.5-23.81h52.53c10.45 0 18.97 8.497 18.97 18.95c0 3.5-1.11 4.94-1.11 9.456c0 26.97 29.77 17.91 29.77 40.64c0 9.254-6.392 10.96-6.392 22.25c0 13.97 10.85 21.95 19.58 23.59c8.953 1.671 15.45 9.481 15.45 18.56c0 13.04-11.39 13.37-11.39 28.91c0 12.54 9.702 23.08 22.36 23.94C456.2 266.1 464 275.2 464 284.1c0 10.43-8.516 18.93-18.97 18.93H307.4c-12.44 0-24 10.02-24 23.1c0 4.038 1.02 8.078 3.066 11.72C304.4 371.7 312 403.8 312 411.2c0 8.044-5.984 20.79-22.06 20.79c-12.53 0-14.27-.9059-24.94-28.07c-24.75-62.91-61.74-99.9-80.98-99.9c-13.8 0-24.02 11.27-24.02 23.99c0 7.041 3.083 14.02 9.016 18.76C238.1 402 211.4 480 289.9 480C333.8 480 360 445 360 411.2c0-12.7-5.328-35.21-14.83-59.33h99.86C481.1 351.9 512 321.9 512 284.1C512 261.8 499.9 241 481.5 229.1z\"/><\/svg>","<svg aria-hidden=\"true\" role=\"img\" viewBox=\"0 0 512 512\" style=\"height:1em;width:1em;vertical-align:-0.125em;margin-left:auto;margin-right:auto;font-size:inherit;fill:currentColor;overflow:visible;position:relative;\"><path d=\"M96 191.1H32c-17.67 0-32 14.33-32 31.1v223.1c0 17.67 14.33 31.1 32 31.1h64c17.67 0 32-14.33 32-31.1V223.1C128 206.3 113.7 191.1 96 191.1zM512 227c0-36.89-30.05-66.92-66.97-66.92h-99.86C354.7 135.1 360 113.5 360 100.8c0-33.8-26.2-68.78-70.06-68.78c-46.61 0-59.36 32.44-69.61 58.5c-31.66 80.5-60.33 66.39-60.33 93.47c0 12.84 10.36 23.99 24.02 23.99c5.256 0 10.55-1.721 14.97-5.26c76.76-61.37 57.97-122.7 90.95-122.7c16.08 0 22.06 12.75 22.06 20.79c0 7.404-7.594 39.55-25.55 71.59c-2.046 3.646-3.066 7.686-3.066 11.72c0 13.92 11.43 23.1 24 23.1h137.6C455.5 208.1 464 216.6 464 227c0 9.809-7.766 18.03-17.67 18.71c-12.66 .8593-22.36 11.4-22.36 23.94c0 15.47 11.39 15.95 11.39 28.91c0 25.37-35.03 12.34-35.03 42.15c0 11.22 6.392 13.03 6.392 22.25c0 22.66-29.77 13.76-29.77 40.64c0 4.515 1.11 5.961 1.11 9.456c0 10.45-8.516 18.95-18.97 18.95h-52.53c-25.62 0-51.02-8.466-71.5-23.81l-36.66-27.51c-4.315-3.245-9.37-4.811-14.38-4.811c-13.85 0-24.03 11.38-24.03 24.04c0 7.287 3.312 14.42 9.596 19.13l36.67 27.52C235 468.1 270.6 480 306.6 480h52.53c35.33 0 64.36-27.49 66.8-62.2c17.77-12.23 28.83-32.51 28.83-54.83c0-3.046-.2187-6.107-.6406-9.122c17.84-12.15 29.28-32.58 29.28-55.28c0-5.311-.6406-10.54-1.875-15.64C499.9 270.1 512 250.2 512 227z\"/><\/svg>","<svg aria-hidden=\"true\" role=\"img\" viewBox=\"0 0 512 512\" style=\"height:1em;width:1em;vertical-align:-0.125em;margin-left:auto;margin-right:auto;font-size:inherit;fill:currentColor;overflow:visible;position:relative;\"><path d=\"M128 288V64.03c0-17.67-14.33-31.1-32-31.1H32c-17.67 0-32 14.33-32 31.1v223.1c0 17.67 14.33 31.1 32 31.1h64C113.7 320 128 305.7 128 288zM481.5 229.1c1.234-5.092 1.875-10.32 1.875-15.64c0-22.7-11.44-43.13-29.28-55.28c.4219-3.015 .6406-6.076 .6406-9.122c0-22.32-11.06-42.6-28.83-54.83c-2.438-34.71-31.47-62.2-66.8-62.2h-52.53c-35.94 0-71.55 11.87-100.3 33.41L169.6 92.93c-6.285 4.71-9.596 11.85-9.596 19.13c0 12.76 10.29 24.04 24.03 24.04c5.013 0 10.07-1.565 14.38-4.811l36.66-27.51c20.48-15.34 45.88-23.81 71.5-23.81h52.53c10.45 0 18.97 8.497 18.97 18.95c0 3.5-1.11 4.94-1.11 9.456c0 26.97 29.77 17.91 29.77 40.64c0 9.254-6.392 10.96-6.392 22.25c0 13.97 10.85 21.95 19.58 23.59c8.953 1.671 15.45 9.481 15.45 18.56c0 13.04-11.39 13.37-11.39 28.91c0 12.54 9.702 23.08 22.36 23.94C456.2 266.1 464 275.2 464 284.1c0 10.43-8.516 18.93-18.97 18.93H307.4c-12.44 0-24 10.02-24 23.1c0 4.038 1.02 8.078 3.066 11.72C304.4 371.7 312 403.8 312 411.2c0 8.044-5.984 20.79-22.06 20.79c-12.53 0-14.27-.9059-24.94-28.07c-24.75-62.91-61.74-99.9-80.98-99.9c-13.8 0-24.02 11.27-24.02 23.99c0 7.041 3.083 14.02 9.016 18.76C238.1 402 211.4 480 289.9 480C333.8 480 360 445 360 411.2c0-12.7-5.328-35.21-14.83-59.33h99.86C481.1 351.9 512 321.9 512 284.1C512 261.8 499.9 241 481.5 229.1z\"/><\/svg>","<svg aria-hidden=\"true\" role=\"img\" viewBox=\"0 0 512 512\" style=\"height:1em;width:1em;vertical-align:-0.125em;margin-left:auto;margin-right:auto;font-size:inherit;fill:currentColor;overflow:visible;position:relative;\"><path d=\"M96 191.1H32c-17.67 0-32 14.33-32 31.1v223.1c0 17.67 14.33 31.1 32 31.1h64c17.67 0 32-14.33 32-31.1V223.1C128 206.3 113.7 191.1 96 191.1zM512 227c0-36.89-30.05-66.92-66.97-66.92h-99.86C354.7 135.1 360 113.5 360 100.8c0-33.8-26.2-68.78-70.06-68.78c-46.61 0-59.36 32.44-69.61 58.5c-31.66 80.5-60.33 66.39-60.33 93.47c0 12.84 10.36 23.99 24.02 23.99c5.256 0 10.55-1.721 14.97-5.26c76.76-61.37 57.97-122.7 90.95-122.7c16.08 0 22.06 12.75 22.06 20.79c0 7.404-7.594 39.55-25.55 71.59c-2.046 3.646-3.066 7.686-3.066 11.72c0 13.92 11.43 23.1 24 23.1h137.6C455.5 208.1 464 216.6 464 227c0 9.809-7.766 18.03-17.67 18.71c-12.66 .8593-22.36 11.4-22.36 23.94c0 15.47 11.39 15.95 11.39 28.91c0 25.37-35.03 12.34-35.03 42.15c0 11.22 6.392 13.03 6.392 22.25c0 22.66-29.77 13.76-29.77 40.64c0 4.515 1.11 5.961 1.11 9.456c0 10.45-8.516 18.95-18.97 18.95h-52.53c-25.62 0-51.02-8.466-71.5-23.81l-36.66-27.51c-4.315-3.245-9.37-4.811-14.38-4.811c-13.85 0-24.03 11.38-24.03 24.04c0 7.287 3.312 14.42 9.596 19.13l36.67 27.52C235 468.1 270.6 480 306.6 480h52.53c35.33 0 64.36-27.49 66.8-62.2c17.77-12.23 28.83-32.51 28.83-54.83c0-3.046-.2187-6.107-.6406-9.122c17.84-12.15 29.28-32.58 29.28-55.28c0-5.311-.6406-10.54-1.875-15.64C499.9 270.1 512 250.2 512 227z\"/><\/svg>","<svg aria-hidden=\"true\" role=\"img\" viewBox=\"0 0 512 512\" style=\"height:1em;width:1em;vertical-align:-0.125em;margin-left:auto;margin-right:auto;font-size:inherit;fill:currentColor;overflow:visible;position:relative;\"><path d=\"M128 288V64.03c0-17.67-14.33-31.1-32-31.1H32c-17.67 0-32 14.33-32 31.1v223.1c0 17.67 14.33 31.1 32 31.1h64C113.7 320 128 305.7 128 288zM481.5 229.1c1.234-5.092 1.875-10.32 1.875-15.64c0-22.7-11.44-43.13-29.28-55.28c.4219-3.015 .6406-6.076 .6406-9.122c0-22.32-11.06-42.6-28.83-54.83c-2.438-34.71-31.47-62.2-66.8-62.2h-52.53c-35.94 0-71.55 11.87-100.3 33.41L169.6 92.93c-6.285 4.71-9.596 11.85-9.596 19.13c0 12.76 10.29 24.04 24.03 24.04c5.013 0 10.07-1.565 14.38-4.811l36.66-27.51c20.48-15.34 45.88-23.81 71.5-23.81h52.53c10.45 0 18.97 8.497 18.97 18.95c0 3.5-1.11 4.94-1.11 9.456c0 26.97 29.77 17.91 29.77 40.64c0 9.254-6.392 10.96-6.392 22.25c0 13.97 10.85 21.95 19.58 23.59c8.953 1.671 15.45 9.481 15.45 18.56c0 13.04-11.39 13.37-11.39 28.91c0 12.54 9.702 23.08 22.36 23.94C456.2 266.1 464 275.2 464 284.1c0 10.43-8.516 18.93-18.97 18.93H307.4c-12.44 0-24 10.02-24 23.1c0 4.038 1.02 8.078 3.066 11.72C304.4 371.7 312 403.8 312 411.2c0 8.044-5.984 20.79-22.06 20.79c-12.53 0-14.27-.9059-24.94-28.07c-24.75-62.91-61.74-99.9-80.98-99.9c-13.8 0-24.02 11.27-24.02 23.99c0 7.041 3.083 14.02 9.016 18.76C238.1 402 211.4 480 289.9 480C333.8 480 360 445 360 411.2c0-12.7-5.328-35.21-14.83-59.33h99.86C481.1 351.9 512 321.9 512 284.1C512 261.8 499.9 241 481.5 229.1z\"/><\/svg>","<svg aria-hidden=\"true\" role=\"img\" viewBox=\"0 0 512 512\" style=\"height:1em;width:1em;vertical-align:-0.125em;margin-left:auto;margin-right:auto;font-size:inherit;fill:currentColor;overflow:visible;position:relative;\"><path d=\"M96 191.1H32c-17.67 0-32 14.33-32 31.1v223.1c0 17.67 14.33 31.1 32 31.1h64c17.67 0 32-14.33 32-31.1V223.1C128 206.3 113.7 191.1 96 191.1zM512 227c0-36.89-30.05-66.92-66.97-66.92h-99.86C354.7 135.1 360 113.5 360 100.8c0-33.8-26.2-68.78-70.06-68.78c-46.61 0-59.36 32.44-69.61 58.5c-31.66 80.5-60.33 66.39-60.33 93.47c0 12.84 10.36 23.99 24.02 23.99c5.256 0 10.55-1.721 14.97-5.26c76.76-61.37 57.97-122.7 90.95-122.7c16.08 0 22.06 12.75 22.06 20.79c0 7.404-7.594 39.55-25.55 71.59c-2.046 3.646-3.066 7.686-3.066 11.72c0 13.92 11.43 23.1 24 23.1h137.6C455.5 208.1 464 216.6 464 227c0 9.809-7.766 18.03-17.67 18.71c-12.66 .8593-22.36 11.4-22.36 23.94c0 15.47 11.39 15.95 11.39 28.91c0 25.37-35.03 12.34-35.03 42.15c0 11.22 6.392 13.03 6.392 22.25c0 22.66-29.77 13.76-29.77 40.64c0 4.515 1.11 5.961 1.11 9.456c0 10.45-8.516 18.95-18.97 18.95h-52.53c-25.62 0-51.02-8.466-71.5-23.81l-36.66-27.51c-4.315-3.245-9.37-4.811-14.38-4.811c-13.85 0-24.03 11.38-24.03 24.04c0 7.287 3.312 14.42 9.596 19.13l36.67 27.52C235 468.1 270.6 480 306.6 480h52.53c35.33 0 64.36-27.49 66.8-62.2c17.77-12.23 28.83-32.51 28.83-54.83c0-3.046-.2187-6.107-.6406-9.122c17.84-12.15 29.28-32.58 29.28-55.28c0-5.311-.6406-10.54-1.875-15.64C499.9 270.1 512 250.2 512 227z\"/><\/svg>","<svg aria-hidden=\"true\" role=\"img\" viewBox=\"0 0 512 512\" style=\"height:1em;width:1em;vertical-align:-0.125em;margin-left:auto;margin-right:auto;font-size:inherit;fill:currentColor;overflow:visible;position:relative;\"><path d=\"M128 288V64.03c0-17.67-14.33-31.1-32-31.1H32c-17.67 0-32 14.33-32 31.1v223.1c0 17.67 14.33 31.1 32 31.1h64C113.7 320 128 305.7 128 288zM481.5 229.1c1.234-5.092 1.875-10.32 1.875-15.64c0-22.7-11.44-43.13-29.28-55.28c.4219-3.015 .6406-6.076 .6406-9.122c0-22.32-11.06-42.6-28.83-54.83c-2.438-34.71-31.47-62.2-66.8-62.2h-52.53c-35.94 0-71.55 11.87-100.3 33.41L169.6 92.93c-6.285 4.71-9.596 11.85-9.596 19.13c0 12.76 10.29 24.04 24.03 24.04c5.013 0 10.07-1.565 14.38-4.811l36.66-27.51c20.48-15.34 45.88-23.81 71.5-23.81h52.53c10.45 0 18.97 8.497 18.97 18.95c0 3.5-1.11 4.94-1.11 9.456c0 26.97 29.77 17.91 29.77 40.64c0 9.254-6.392 10.96-6.392 22.25c0 13.97 10.85 21.95 19.58 23.59c8.953 1.671 15.45 9.481 15.45 18.56c0 13.04-11.39 13.37-11.39 28.91c0 12.54 9.702 23.08 22.36 23.94C456.2 266.1 464 275.2 464 284.1c0 10.43-8.516 18.93-18.97 18.93H307.4c-12.44 0-24 10.02-24 23.1c0 4.038 1.02 8.078 3.066 11.72C304.4 371.7 312 403.8 312 411.2c0 8.044-5.984 20.79-22.06 20.79c-12.53 0-14.27-.9059-24.94-28.07c-24.75-62.91-61.74-99.9-80.98-99.9c-13.8 0-24.02 11.27-24.02 23.99c0 7.041 3.083 14.02 9.016 18.76C238.1 402 211.4 480 289.9 480C333.8 480 360 445 360 411.2c0-12.7-5.328-35.21-14.83-59.33h99.86C481.1 351.9 512 321.9 512 284.1C512 261.8 499.9 241 481.5 229.1z\"/><\/svg>","<svg aria-hidden=\"true\" role=\"img\" viewBox=\"0 0 512 512\" style=\"height:1em;width:1em;vertical-align:-0.125em;margin-left:auto;margin-right:auto;font-size:inherit;fill:currentColor;overflow:visible;position:relative;\"><path d=\"M96 191.1H32c-17.67 0-32 14.33-32 31.1v223.1c0 17.67 14.33 31.1 32 31.1h64c17.67 0 32-14.33 32-31.1V223.1C128 206.3 113.7 191.1 96 191.1zM512 227c0-36.89-30.05-66.92-66.97-66.92h-99.86C354.7 135.1 360 113.5 360 100.8c0-33.8-26.2-68.78-70.06-68.78c-46.61 0-59.36 32.44-69.61 58.5c-31.66 80.5-60.33 66.39-60.33 93.47c0 12.84 10.36 23.99 24.02 23.99c5.256 0 10.55-1.721 14.97-5.26c76.76-61.37 57.97-122.7 90.95-122.7c16.08 0 22.06 12.75 22.06 20.79c0 7.404-7.594 39.55-25.55 71.59c-2.046 3.646-3.066 7.686-3.066 11.72c0 13.92 11.43 23.1 24 23.1h137.6C455.5 208.1 464 216.6 464 227c0 9.809-7.766 18.03-17.67 18.71c-12.66 .8593-22.36 11.4-22.36 23.94c0 15.47 11.39 15.95 11.39 28.91c0 25.37-35.03 12.34-35.03 42.15c0 11.22 6.392 13.03 6.392 22.25c0 22.66-29.77 13.76-29.77 40.64c0 4.515 1.11 5.961 1.11 9.456c0 10.45-8.516 18.95-18.97 18.95h-52.53c-25.62 0-51.02-8.466-71.5-23.81l-36.66-27.51c-4.315-3.245-9.37-4.811-14.38-4.811c-13.85 0-24.03 11.38-24.03 24.04c0 7.287 3.312 14.42 9.596 19.13l36.67 27.52C235 468.1 270.6 480 306.6 480h52.53c35.33 0 64.36-27.49 66.8-62.2c17.77-12.23 28.83-32.51 28.83-54.83c0-3.046-.2187-6.107-.6406-9.122c17.84-12.15 29.28-32.58 29.28-55.28c0-5.311-.6406-10.54-1.875-15.64C499.9 270.1 512 250.2 512 227z\"/><\/svg>","<svg aria-hidden=\"true\" role=\"img\" viewBox=\"0 0 512 512\" style=\"height:1em;width:1em;vertical-align:-0.125em;margin-left:auto;margin-right:auto;font-size:inherit;fill:currentColor;overflow:visible;position:relative;\"><path d=\"M128 288V64.03c0-17.67-14.33-31.1-32-31.1H32c-17.67 0-32 14.33-32 31.1v223.1c0 17.67 14.33 31.1 32 31.1h64C113.7 320 128 305.7 128 288zM481.5 229.1c1.234-5.092 1.875-10.32 1.875-15.64c0-22.7-11.44-43.13-29.28-55.28c.4219-3.015 .6406-6.076 .6406-9.122c0-22.32-11.06-42.6-28.83-54.83c-2.438-34.71-31.47-62.2-66.8-62.2h-52.53c-35.94 0-71.55 11.87-100.3 33.41L169.6 92.93c-6.285 4.71-9.596 11.85-9.596 19.13c0 12.76 10.29 24.04 24.03 24.04c5.013 0 10.07-1.565 14.38-4.811l36.66-27.51c20.48-15.34 45.88-23.81 71.5-23.81h52.53c10.45 0 18.97 8.497 18.97 18.95c0 3.5-1.11 4.94-1.11 9.456c0 26.97 29.77 17.91 29.77 40.64c0 9.254-6.392 10.96-6.392 22.25c0 13.97 10.85 21.95 19.58 23.59c8.953 1.671 15.45 9.481 15.45 18.56c0 13.04-11.39 13.37-11.39 28.91c0 12.54 9.702 23.08 22.36 23.94C456.2 266.1 464 275.2 464 284.1c0 10.43-8.516 18.93-18.97 18.93H307.4c-12.44 0-24 10.02-24 23.1c0 4.038 1.02 8.078 3.066 11.72C304.4 371.7 312 403.8 312 411.2c0 8.044-5.984 20.79-22.06 20.79c-12.53 0-14.27-.9059-24.94-28.07c-24.75-62.91-61.74-99.9-80.98-99.9c-13.8 0-24.02 11.27-24.02 23.99c0 7.041 3.083 14.02 9.016 18.76C238.1 402 211.4 480 289.9 480C333.8 480 360 445 360 411.2c0-12.7-5.328-35.21-14.83-59.33h99.86C481.1 351.9 512 321.9 512 284.1C512 261.8 499.9 241 481.5 229.1z\"/><\/svg>","<svg aria-hidden=\"true\" role=\"img\" viewBox=\"0 0 512 512\" style=\"height:1em;width:1em;vertical-align:-0.125em;margin-left:auto;margin-right:auto;font-size:inherit;fill:currentColor;overflow:visible;position:relative;\"><path d=\"M96 191.1H32c-17.67 0-32 14.33-32 31.1v223.1c0 17.67 14.33 31.1 32 31.1h64c17.67 0 32-14.33 32-31.1V223.1C128 206.3 113.7 191.1 96 191.1zM512 227c0-36.89-30.05-66.92-66.97-66.92h-99.86C354.7 135.1 360 113.5 360 100.8c0-33.8-26.2-68.78-70.06-68.78c-46.61 0-59.36 32.44-69.61 58.5c-31.66 80.5-60.33 66.39-60.33 93.47c0 12.84 10.36 23.99 24.02 23.99c5.256 0 10.55-1.721 14.97-5.26c76.76-61.37 57.97-122.7 90.95-122.7c16.08 0 22.06 12.75 22.06 20.79c0 7.404-7.594 39.55-25.55 71.59c-2.046 3.646-3.066 7.686-3.066 11.72c0 13.92 11.43 23.1 24 23.1h137.6C455.5 208.1 464 216.6 464 227c0 9.809-7.766 18.03-17.67 18.71c-12.66 .8593-22.36 11.4-22.36 23.94c0 15.47 11.39 15.95 11.39 28.91c0 25.37-35.03 12.34-35.03 42.15c0 11.22 6.392 13.03 6.392 22.25c0 22.66-29.77 13.76-29.77 40.64c0 4.515 1.11 5.961 1.11 9.456c0 10.45-8.516 18.95-18.97 18.95h-52.53c-25.62 0-51.02-8.466-71.5-23.81l-36.66-27.51c-4.315-3.245-9.37-4.811-14.38-4.811c-13.85 0-24.03 11.38-24.03 24.04c0 7.287 3.312 14.42 9.596 19.13l36.67 27.52C235 468.1 270.6 480 306.6 480h52.53c35.33 0 64.36-27.49 66.8-62.2c17.77-12.23 28.83-32.51 28.83-54.83c0-3.046-.2187-6.107-.6406-9.122c17.84-12.15 29.28-32.58 29.28-55.28c0-5.311-.6406-10.54-1.875-15.64C499.9 270.1 512 250.2 512 227z\"/><\/svg>"]],"container":"<table class=\"display\">\n  <thead>\n    <tr>\n      <th> <\/th>\n      <th>type1<\/th>\n      <th>type2<\/th>\n      <th>value<\/th>\n      <th>value1<\/th>\n      <th>value2<\/th>\n      <th>prob1<\/th>\n      <th>prob2<\/th>\n      <th>level<\/th>\n    <\/tr>\n  <\/thead>\n<\/table>","options":{"pageLength":5,"dom":"ftip","columnDefs":[{"className":"dt-right","targets":[3,4,5,6,7]},{"orderable":false,"targets":0}],"order":[],"autoWidth":false,"orderClasses":false,"lengthMenu":[5,10,25,50,100]}},"evals":[],"jsHooks":[]}</script>

-   插入多个字体图标，即把单个字体图标拼贴到一起。

``` r
icon2 <- as.data.table(data)

icon2 <- icon2[, ':='(score = sample(1:5, 40, replace = TRUE))]

icon2$score <- strrep(fontawesome::fa(name = "heart"), icon2$score)

datatable(icon2, escape = FALSE)
```

<div id="htmlwidget-42" style="width:100%;height:auto;" class="datatables html-widget"></div>
<script type="application/json" data-for="htmlwidget-42">{"x":{"filter":"none","vertical":false,"data":[["1","2","3","4","5","6","7","8","9","10","11","12","13","14","15","16","17","18","19","20","21","22","23","24","25","26","27","28","29","30","31","32","33","34","35","36","37","38","39","40"],["A","A","B","B","C","C","D","D","E","E","F","F","G","G","H","H","I","I","J","J","K","K","L","L","M","M","N","N","O","O","P","P","Q","Q","R","R","S","S","T","T"],["NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES"],[2227,3458,4870,2707,2773,4750,2475,2122,4280,3293,3271,3521,2950,4159,4517,3988,2512,2799,4496,4425,4716,3547,3998,2827,2427,3989,2358,4197,2987,3130,2275,3597,3607,4499,2796,2193,4631,2492,4303,2233],[1134,1576,1510,1279,1224,581,1242,700,1529,624,1584,1471,202,1211,1726,1255,1855,616,1834,1953,987,1441,798,1542,550,1715,1100,1047,1777,1929,543,735,1688,1683,345,1601,1420,1333,1229,958],[1502,1327,1647,1188,1430,1768,806,1875,565,1024,528,1258,603,490,935,438,301,1751,1161,1276,1606,1665,376,783,1143,1560,1571,663,697,1596,726,1128,313,1410,1020,1444,1935,1816,1346,912],[0.39,0.02,0.19,0.29,0.54,0.03,0.04,0.36,0.47,0.38,0.69,0.65,0.46,0.2,0.26,0.77,0.86,0.59,0.22,0.34,0.63,0.83,0.89,0.42,0.94,0.45,0.95,0.58,0.01,0.28,0.32,0.96,0.07,0.76,0.13,0.05,0.85,0.75,0.31,0.23],[-0.02,0.01,0.28,0.12,0.32,0,-0.5,-0.01,0.27,0.24,-0.11,-0.4,-0.06,0.31,0.15,0.41,0.42,-0.05,-0.16,-0.48,0.18,-0.45,0.05,0.02,0.43,0.04,-0.46,-0.25,-0.14,0.37,0.16,-0.34,-0.32,0.44,0.26,-0.43,-0.13,-0.42,-0.09,-0.2],["<svg aria-hidden=\"true\" role=\"img\" viewBox=\"0 0 512 512\" style=\"height:1em;width:1em;vertical-align:-0.125em;margin-left:auto;margin-right:auto;font-size:inherit;fill:currentColor;overflow:visible;position:relative;\"><path d=\"M244 84L255.1 96L267.1 84.02C300.6 51.37 347 36.51 392.6 44.1C461.5 55.58 512 115.2 512 185.1V190.9C512 232.4 494.8 272.1 464.4 300.4L283.7 469.1C276.2 476.1 266.3 480 256 480C245.7 480 235.8 476.1 228.3 469.1L47.59 300.4C17.23 272.1 0 232.4 0 190.9V185.1C0 115.2 50.52 55.58 119.4 44.1C164.1 36.51 211.4 51.37 244 84C243.1 84 244 84.01 244 84L244 84zM255.1 163.9L210.1 117.1C188.4 96.28 157.6 86.4 127.3 91.44C81.55 99.07 48 138.7 48 185.1V190.9C48 219.1 59.71 246.1 80.34 265.3L256 429.3L431.7 265.3C452.3 246.1 464 219.1 464 190.9V185.1C464 138.7 430.4 99.07 384.7 91.44C354.4 86.4 323.6 96.28 301.9 117.1L255.1 163.9z\"/><\/svg><svg aria-hidden=\"true\" role=\"img\" viewBox=\"0 0 512 512\" style=\"height:1em;width:1em;vertical-align:-0.125em;margin-left:auto;margin-right:auto;font-size:inherit;fill:currentColor;overflow:visible;position:relative;\"><path d=\"M244 84L255.1 96L267.1 84.02C300.6 51.37 347 36.51 392.6 44.1C461.5 55.58 512 115.2 512 185.1V190.9C512 232.4 494.8 272.1 464.4 300.4L283.7 469.1C276.2 476.1 266.3 480 256 480C245.7 480 235.8 476.1 228.3 469.1L47.59 300.4C17.23 272.1 0 232.4 0 190.9V185.1C0 115.2 50.52 55.58 119.4 44.1C164.1 36.51 211.4 51.37 244 84C243.1 84 244 84.01 244 84L244 84zM255.1 163.9L210.1 117.1C188.4 96.28 157.6 86.4 127.3 91.44C81.55 99.07 48 138.7 48 185.1V190.9C48 219.1 59.71 246.1 80.34 265.3L256 429.3L431.7 265.3C452.3 246.1 464 219.1 464 190.9V185.1C464 138.7 430.4 99.07 384.7 91.44C354.4 86.4 323.6 96.28 301.9 117.1L255.1 163.9z\"/><\/svg><svg aria-hidden=\"true\" role=\"img\" viewBox=\"0 0 512 512\" style=\"height:1em;width:1em;vertical-align:-0.125em;margin-left:auto;margin-right:auto;font-size:inherit;fill:currentColor;overflow:visible;position:relative;\"><path d=\"M244 84L255.1 96L267.1 84.02C300.6 51.37 347 36.51 392.6 44.1C461.5 55.58 512 115.2 512 185.1V190.9C512 232.4 494.8 272.1 464.4 300.4L283.7 469.1C276.2 476.1 266.3 480 256 480C245.7 480 235.8 476.1 228.3 469.1L47.59 300.4C17.23 272.1 0 232.4 0 190.9V185.1C0 115.2 50.52 55.58 119.4 44.1C164.1 36.51 211.4 51.37 244 84C243.1 84 244 84.01 244 84L244 84zM255.1 163.9L210.1 117.1C188.4 96.28 157.6 86.4 127.3 91.44C81.55 99.07 48 138.7 48 185.1V190.9C48 219.1 59.71 246.1 80.34 265.3L256 429.3L431.7 265.3C452.3 246.1 464 219.1 464 190.9V185.1C464 138.7 430.4 99.07 384.7 91.44C354.4 86.4 323.6 96.28 301.9 117.1L255.1 163.9z\"/><\/svg>","<svg aria-hidden=\"true\" role=\"img\" viewBox=\"0 0 512 512\" style=\"height:1em;width:1em;vertical-align:-0.125em;margin-left:auto;margin-right:auto;font-size:inherit;fill:currentColor;overflow:visible;position:relative;\"><path d=\"M244 84L255.1 96L267.1 84.02C300.6 51.37 347 36.51 392.6 44.1C461.5 55.58 512 115.2 512 185.1V190.9C512 232.4 494.8 272.1 464.4 300.4L283.7 469.1C276.2 476.1 266.3 480 256 480C245.7 480 235.8 476.1 228.3 469.1L47.59 300.4C17.23 272.1 0 232.4 0 190.9V185.1C0 115.2 50.52 55.58 119.4 44.1C164.1 36.51 211.4 51.37 244 84C243.1 84 244 84.01 244 84L244 84zM255.1 163.9L210.1 117.1C188.4 96.28 157.6 86.4 127.3 91.44C81.55 99.07 48 138.7 48 185.1V190.9C48 219.1 59.71 246.1 80.34 265.3L256 429.3L431.7 265.3C452.3 246.1 464 219.1 464 190.9V185.1C464 138.7 430.4 99.07 384.7 91.44C354.4 86.4 323.6 96.28 301.9 117.1L255.1 163.9z\"/><\/svg><svg aria-hidden=\"true\" role=\"img\" viewBox=\"0 0 512 512\" style=\"height:1em;width:1em;vertical-align:-0.125em;margin-left:auto;margin-right:auto;font-size:inherit;fill:currentColor;overflow:visible;position:relative;\"><path d=\"M244 84L255.1 96L267.1 84.02C300.6 51.37 347 36.51 392.6 44.1C461.5 55.58 512 115.2 512 185.1V190.9C512 232.4 494.8 272.1 464.4 300.4L283.7 469.1C276.2 476.1 266.3 480 256 480C245.7 480 235.8 476.1 228.3 469.1L47.59 300.4C17.23 272.1 0 232.4 0 190.9V185.1C0 115.2 50.52 55.58 119.4 44.1C164.1 36.51 211.4 51.37 244 84C243.1 84 244 84.01 244 84L244 84zM255.1 163.9L210.1 117.1C188.4 96.28 157.6 86.4 127.3 91.44C81.55 99.07 48 138.7 48 185.1V190.9C48 219.1 59.71 246.1 80.34 265.3L256 429.3L431.7 265.3C452.3 246.1 464 219.1 464 190.9V185.1C464 138.7 430.4 99.07 384.7 91.44C354.4 86.4 323.6 96.28 301.9 117.1L255.1 163.9z\"/><\/svg><svg aria-hidden=\"true\" role=\"img\" viewBox=\"0 0 512 512\" style=\"height:1em;width:1em;vertical-align:-0.125em;margin-left:auto;margin-right:auto;font-size:inherit;fill:currentColor;overflow:visible;position:relative;\"><path d=\"M244 84L255.1 96L267.1 84.02C300.6 51.37 347 36.51 392.6 44.1C461.5 55.58 512 115.2 512 185.1V190.9C512 232.4 494.8 272.1 464.4 300.4L283.7 469.1C276.2 476.1 266.3 480 256 480C245.7 480 235.8 476.1 228.3 469.1L47.59 300.4C17.23 272.1 0 232.4 0 190.9V185.1C0 115.2 50.52 55.58 119.4 44.1C164.1 36.51 211.4 51.37 244 84C243.1 84 244 84.01 244 84L244 84zM255.1 163.9L210.1 117.1C188.4 96.28 157.6 86.4 127.3 91.44C81.55 99.07 48 138.7 48 185.1V190.9C48 219.1 59.71 246.1 80.34 265.3L256 429.3L431.7 265.3C452.3 246.1 464 219.1 464 190.9V185.1C464 138.7 430.4 99.07 384.7 91.44C354.4 86.4 323.6 96.28 301.9 117.1L255.1 163.9z\"/><\/svg><svg aria-hidden=\"true\" role=\"img\" viewBox=\"0 0 512 512\" style=\"height:1em;width:1em;vertical-align:-0.125em;margin-left:auto;margin-right:auto;font-size:inherit;fill:currentColor;overflow:visible;position:relative;\"><path d=\"M244 84L255.1 96L267.1 84.02C300.6 51.37 347 36.51 392.6 44.1C461.5 55.58 512 115.2 512 185.1V190.9C512 232.4 494.8 272.1 464.4 300.4L283.7 469.1C276.2 476.1 266.3 480 256 480C245.7 480 235.8 476.1 228.3 469.1L47.59 300.4C17.23 272.1 0 232.4 0 190.9V185.1C0 115.2 50.52 55.58 119.4 44.1C164.1 36.51 211.4 51.37 244 84C243.1 84 244 84.01 244 84L244 84zM255.1 163.9L210.1 117.1C188.4 96.28 157.6 86.4 127.3 91.44C81.55 99.07 48 138.7 48 185.1V190.9C48 219.1 59.71 246.1 80.34 265.3L256 429.3L431.7 265.3C452.3 246.1 464 219.1 464 190.9V185.1C464 138.7 430.4 99.07 384.7 91.44C354.4 86.4 323.6 96.28 301.9 117.1L255.1 163.9z\"/><\/svg>","<svg aria-hidden=\"true\" role=\"img\" viewBox=\"0 0 512 512\" style=\"height:1em;width:1em;vertical-align:-0.125em;margin-left:auto;margin-right:auto;font-size:inherit;fill:currentColor;overflow:visible;position:relative;\"><path d=\"M244 84L255.1 96L267.1 84.02C300.6 51.37 347 36.51 392.6 44.1C461.5 55.58 512 115.2 512 185.1V190.9C512 232.4 494.8 272.1 464.4 300.4L283.7 469.1C276.2 476.1 266.3 480 256 480C245.7 480 235.8 476.1 228.3 469.1L47.59 300.4C17.23 272.1 0 232.4 0 190.9V185.1C0 115.2 50.52 55.58 119.4 44.1C164.1 36.51 211.4 51.37 244 84C243.1 84 244 84.01 244 84L244 84zM255.1 163.9L210.1 117.1C188.4 96.28 157.6 86.4 127.3 91.44C81.55 99.07 48 138.7 48 185.1V190.9C48 219.1 59.71 246.1 80.34 265.3L256 429.3L431.7 265.3C452.3 246.1 464 219.1 464 190.9V185.1C464 138.7 430.4 99.07 384.7 91.44C354.4 86.4 323.6 96.28 301.9 117.1L255.1 163.9z\"/><\/svg><svg aria-hidden=\"true\" role=\"img\" viewBox=\"0 0 512 512\" style=\"height:1em;width:1em;vertical-align:-0.125em;margin-left:auto;margin-right:auto;font-size:inherit;fill:currentColor;overflow:visible;position:relative;\"><path d=\"M244 84L255.1 96L267.1 84.02C300.6 51.37 347 36.51 392.6 44.1C461.5 55.58 512 115.2 512 185.1V190.9C512 232.4 494.8 272.1 464.4 300.4L283.7 469.1C276.2 476.1 266.3 480 256 480C245.7 480 235.8 476.1 228.3 469.1L47.59 300.4C17.23 272.1 0 232.4 0 190.9V185.1C0 115.2 50.52 55.58 119.4 44.1C164.1 36.51 211.4 51.37 244 84C243.1 84 244 84.01 244 84L244 84zM255.1 163.9L210.1 117.1C188.4 96.28 157.6 86.4 127.3 91.44C81.55 99.07 48 138.7 48 185.1V190.9C48 219.1 59.71 246.1 80.34 265.3L256 429.3L431.7 265.3C452.3 246.1 464 219.1 464 190.9V185.1C464 138.7 430.4 99.07 384.7 91.44C354.4 86.4 323.6 96.28 301.9 117.1L255.1 163.9z\"/><\/svg><svg aria-hidden=\"true\" role=\"img\" viewBox=\"0 0 512 512\" style=\"height:1em;width:1em;vertical-align:-0.125em;margin-left:auto;margin-right:auto;font-size:inherit;fill:currentColor;overflow:visible;position:relative;\"><path d=\"M244 84L255.1 96L267.1 84.02C300.6 51.37 347 36.51 392.6 44.1C461.5 55.58 512 115.2 512 185.1V190.9C512 232.4 494.8 272.1 464.4 300.4L283.7 469.1C276.2 476.1 266.3 480 256 480C245.7 480 235.8 476.1 228.3 469.1L47.59 300.4C17.23 272.1 0 232.4 0 190.9V185.1C0 115.2 50.52 55.58 119.4 44.1C164.1 36.51 211.4 51.37 244 84C243.1 84 244 84.01 244 84L244 84zM255.1 163.9L210.1 117.1C188.4 96.28 157.6 86.4 127.3 91.44C81.55 99.07 48 138.7 48 185.1V190.9C48 219.1 59.71 246.1 80.34 265.3L256 429.3L431.7 265.3C452.3 246.1 464 219.1 464 190.9V185.1C464 138.7 430.4 99.07 384.7 91.44C354.4 86.4 323.6 96.28 301.9 117.1L255.1 163.9z\"/><\/svg>","<svg aria-hidden=\"true\" role=\"img\" viewBox=\"0 0 512 512\" style=\"height:1em;width:1em;vertical-align:-0.125em;margin-left:auto;margin-right:auto;font-size:inherit;fill:currentColor;overflow:visible;position:relative;\"><path d=\"M244 84L255.1 96L267.1 84.02C300.6 51.37 347 36.51 392.6 44.1C461.5 55.58 512 115.2 512 185.1V190.9C512 232.4 494.8 272.1 464.4 300.4L283.7 469.1C276.2 476.1 266.3 480 256 480C245.7 480 235.8 476.1 228.3 469.1L47.59 300.4C17.23 272.1 0 232.4 0 190.9V185.1C0 115.2 50.52 55.58 119.4 44.1C164.1 36.51 211.4 51.37 244 84C243.1 84 244 84.01 244 84L244 84zM255.1 163.9L210.1 117.1C188.4 96.28 157.6 86.4 127.3 91.44C81.55 99.07 48 138.7 48 185.1V190.9C48 219.1 59.71 246.1 80.34 265.3L256 429.3L431.7 265.3C452.3 246.1 464 219.1 464 190.9V185.1C464 138.7 430.4 99.07 384.7 91.44C354.4 86.4 323.6 96.28 301.9 117.1L255.1 163.9z\"/><\/svg><svg aria-hidden=\"true\" role=\"img\" viewBox=\"0 0 512 512\" style=\"height:1em;width:1em;vertical-align:-0.125em;margin-left:auto;margin-right:auto;font-size:inherit;fill:currentColor;overflow:visible;position:relative;\"><path d=\"M244 84L255.1 96L267.1 84.02C300.6 51.37 347 36.51 392.6 44.1C461.5 55.58 512 115.2 512 185.1V190.9C512 232.4 494.8 272.1 464.4 300.4L283.7 469.1C276.2 476.1 266.3 480 256 480C245.7 480 235.8 476.1 228.3 469.1L47.59 300.4C17.23 272.1 0 232.4 0 190.9V185.1C0 115.2 50.52 55.58 119.4 44.1C164.1 36.51 211.4 51.37 244 84C243.1 84 244 84.01 244 84L244 84zM255.1 163.9L210.1 117.1C188.4 96.28 157.6 86.4 127.3 91.44C81.55 99.07 48 138.7 48 185.1V190.9C48 219.1 59.71 246.1 80.34 265.3L256 429.3L431.7 265.3C452.3 246.1 464 219.1 464 190.9V185.1C464 138.7 430.4 99.07 384.7 91.44C354.4 86.4 323.6 96.28 301.9 117.1L255.1 163.9z\"/><\/svg><svg aria-hidden=\"true\" role=\"img\" viewBox=\"0 0 512 512\" style=\"height:1em;width:1em;vertical-align:-0.125em;margin-left:auto;margin-right:auto;font-size:inherit;fill:currentColor;overflow:visible;position:relative;\"><path d=\"M244 84L255.1 96L267.1 84.02C300.6 51.37 347 36.51 392.6 44.1C461.5 55.58 512 115.2 512 185.1V190.9C512 232.4 494.8 272.1 464.4 300.4L283.7 469.1C276.2 476.1 266.3 480 256 480C245.7 480 235.8 476.1 228.3 469.1L47.59 300.4C17.23 272.1 0 232.4 0 190.9V185.1C0 115.2 50.52 55.58 119.4 44.1C164.1 36.51 211.4 51.37 244 84C243.1 84 244 84.01 244 84L244 84zM255.1 163.9L210.1 117.1C188.4 96.28 157.6 86.4 127.3 91.44C81.55 99.07 48 138.7 48 185.1V190.9C48 219.1 59.71 246.1 80.34 265.3L256 429.3L431.7 265.3C452.3 246.1 464 219.1 464 190.9V185.1C464 138.7 430.4 99.07 384.7 91.44C354.4 86.4 323.6 96.28 301.9 117.1L255.1 163.9z\"/><\/svg><svg aria-hidden=\"true\" role=\"img\" viewBox=\"0 0 512 512\" style=\"height:1em;width:1em;vertical-align:-0.125em;margin-left:auto;margin-right:auto;font-size:inherit;fill:currentColor;overflow:visible;position:relative;\"><path d=\"M244 84L255.1 96L267.1 84.02C300.6 51.37 347 36.51 392.6 44.1C461.5 55.58 512 115.2 512 185.1V190.9C512 232.4 494.8 272.1 464.4 300.4L283.7 469.1C276.2 476.1 266.3 480 256 480C245.7 480 235.8 476.1 228.3 469.1L47.59 300.4C17.23 272.1 0 232.4 0 190.9V185.1C0 115.2 50.52 55.58 119.4 44.1C164.1 36.51 211.4 51.37 244 84C243.1 84 244 84.01 244 84L244 84zM255.1 163.9L210.1 117.1C188.4 96.28 157.6 86.4 127.3 91.44C81.55 99.07 48 138.7 48 185.1V190.9C48 219.1 59.71 246.1 80.34 265.3L256 429.3L431.7 265.3C452.3 246.1 464 219.1 464 190.9V185.1C464 138.7 430.4 99.07 384.7 91.44C354.4 86.4 323.6 96.28 301.9 117.1L255.1 163.9z\"/><\/svg>","<svg aria-hidden=\"true\" role=\"img\" viewBox=\"0 0 512 512\" style=\"height:1em;width:1em;vertical-align:-0.125em;margin-left:auto;margin-right:auto;font-size:inherit;fill:currentColor;overflow:visible;position:relative;\"><path d=\"M244 84L255.1 96L267.1 84.02C300.6 51.37 347 36.51 392.6 44.1C461.5 55.58 512 115.2 512 185.1V190.9C512 232.4 494.8 272.1 464.4 300.4L283.7 469.1C276.2 476.1 266.3 480 256 480C245.7 480 235.8 476.1 228.3 469.1L47.59 300.4C17.23 272.1 0 232.4 0 190.9V185.1C0 115.2 50.52 55.58 119.4 44.1C164.1 36.51 211.4 51.37 244 84C243.1 84 244 84.01 244 84L244 84zM255.1 163.9L210.1 117.1C188.4 96.28 157.6 86.4 127.3 91.44C81.55 99.07 48 138.7 48 185.1V190.9C48 219.1 59.71 246.1 80.34 265.3L256 429.3L431.7 265.3C452.3 246.1 464 219.1 464 190.9V185.1C464 138.7 430.4 99.07 384.7 91.44C354.4 86.4 323.6 96.28 301.9 117.1L255.1 163.9z\"/><\/svg><svg aria-hidden=\"true\" role=\"img\" viewBox=\"0 0 512 512\" style=\"height:1em;width:1em;vertical-align:-0.125em;margin-left:auto;margin-right:auto;font-size:inherit;fill:currentColor;overflow:visible;position:relative;\"><path d=\"M244 84L255.1 96L267.1 84.02C300.6 51.37 347 36.51 392.6 44.1C461.5 55.58 512 115.2 512 185.1V190.9C512 232.4 494.8 272.1 464.4 300.4L283.7 469.1C276.2 476.1 266.3 480 256 480C245.7 480 235.8 476.1 228.3 469.1L47.59 300.4C17.23 272.1 0 232.4 0 190.9V185.1C0 115.2 50.52 55.58 119.4 44.1C164.1 36.51 211.4 51.37 244 84C243.1 84 244 84.01 244 84L244 84zM255.1 163.9L210.1 117.1C188.4 96.28 157.6 86.4 127.3 91.44C81.55 99.07 48 138.7 48 185.1V190.9C48 219.1 59.71 246.1 80.34 265.3L256 429.3L431.7 265.3C452.3 246.1 464 219.1 464 190.9V185.1C464 138.7 430.4 99.07 384.7 91.44C354.4 86.4 323.6 96.28 301.9 117.1L255.1 163.9z\"/><\/svg><svg aria-hidden=\"true\" role=\"img\" viewBox=\"0 0 512 512\" style=\"height:1em;width:1em;vertical-align:-0.125em;margin-left:auto;margin-right:auto;font-size:inherit;fill:currentColor;overflow:visible;position:relative;\"><path d=\"M244 84L255.1 96L267.1 84.02C300.6 51.37 347 36.51 392.6 44.1C461.5 55.58 512 115.2 512 185.1V190.9C512 232.4 494.8 272.1 464.4 300.4L283.7 469.1C276.2 476.1 266.3 480 256 480C245.7 480 235.8 476.1 228.3 469.1L47.59 300.4C17.23 272.1 0 232.4 0 190.9V185.1C0 115.2 50.52 55.58 119.4 44.1C164.1 36.51 211.4 51.37 244 84C243.1 84 244 84.01 244 84L244 84zM255.1 163.9L210.1 117.1C188.4 96.28 157.6 86.4 127.3 91.44C81.55 99.07 48 138.7 48 185.1V190.9C48 219.1 59.71 246.1 80.34 265.3L256 429.3L431.7 265.3C452.3 246.1 464 219.1 464 190.9V185.1C464 138.7 430.4 99.07 384.7 91.44C354.4 86.4 323.6 96.28 301.9 117.1L255.1 163.9z\"/><\/svg><svg aria-hidden=\"true\" role=\"img\" viewBox=\"0 0 512 512\" style=\"height:1em;width:1em;vertical-align:-0.125em;margin-left:auto;margin-right:auto;font-size:inherit;fill:currentColor;overflow:visible;position:relative;\"><path d=\"M244 84L255.1 96L267.1 84.02C300.6 51.37 347 36.51 392.6 44.1C461.5 55.58 512 115.2 512 185.1V190.9C512 232.4 494.8 272.1 464.4 300.4L283.7 469.1C276.2 476.1 266.3 480 256 480C245.7 480 235.8 476.1 228.3 469.1L47.59 300.4C17.23 272.1 0 232.4 0 190.9V185.1C0 115.2 50.52 55.58 119.4 44.1C164.1 36.51 211.4 51.37 244 84C243.1 84 244 84.01 244 84L244 84zM255.1 163.9L210.1 117.1C188.4 96.28 157.6 86.4 127.3 91.44C81.55 99.07 48 138.7 48 185.1V190.9C48 219.1 59.71 246.1 80.34 265.3L256 429.3L431.7 265.3C452.3 246.1 464 219.1 464 190.9V185.1C464 138.7 430.4 99.07 384.7 91.44C354.4 86.4 323.6 96.28 301.9 117.1L255.1 163.9z\"/><\/svg><svg aria-hidden=\"true\" role=\"img\" viewBox=\"0 0 512 512\" style=\"height:1em;width:1em;vertical-align:-0.125em;margin-left:auto;margin-right:auto;font-size:inherit;fill:currentColor;overflow:visible;position:relative;\"><path d=\"M244 84L255.1 96L267.1 84.02C300.6 51.37 347 36.51 392.6 44.1C461.5 55.58 512 115.2 512 185.1V190.9C512 232.4 494.8 272.1 464.4 300.4L283.7 469.1C276.2 476.1 266.3 480 256 480C245.7 480 235.8 476.1 228.3 469.1L47.59 300.4C17.23 272.1 0 232.4 0 190.9V185.1C0 115.2 50.52 55.58 119.4 44.1C164.1 36.51 211.4 51.37 244 84C243.1 84 244 84.01 244 84L244 84zM255.1 163.9L210.1 117.1C188.4 96.28 157.6 86.4 127.3 91.44C81.55 99.07 48 138.7 48 185.1V190.9C48 219.1 59.71 246.1 80.34 265.3L256 429.3L431.7 265.3C452.3 246.1 464 219.1 464 190.9V185.1C464 138.7 430.4 99.07 384.7 91.44C354.4 86.4 323.6 96.28 301.9 117.1L255.1 163.9z\"/><\/svg>","<svg aria-hidden=\"true\" role=\"img\" viewBox=\"0 0 512 512\" style=\"height:1em;width:1em;vertical-align:-0.125em;margin-left:auto;margin-right:auto;font-size:inherit;fill:currentColor;overflow:visible;position:relative;\"><path d=\"M244 84L255.1 96L267.1 84.02C300.6 51.37 347 36.51 392.6 44.1C461.5 55.58 512 115.2 512 185.1V190.9C512 232.4 494.8 272.1 464.4 300.4L283.7 469.1C276.2 476.1 266.3 480 256 480C245.7 480 235.8 476.1 228.3 469.1L47.59 300.4C17.23 272.1 0 232.4 0 190.9V185.1C0 115.2 50.52 55.58 119.4 44.1C164.1 36.51 211.4 51.37 244 84C243.1 84 244 84.01 244 84L244 84zM255.1 163.9L210.1 117.1C188.4 96.28 157.6 86.4 127.3 91.44C81.55 99.07 48 138.7 48 185.1V190.9C48 219.1 59.71 246.1 80.34 265.3L256 429.3L431.7 265.3C452.3 246.1 464 219.1 464 190.9V185.1C464 138.7 430.4 99.07 384.7 91.44C354.4 86.4 323.6 96.28 301.9 117.1L255.1 163.9z\"/><\/svg><svg aria-hidden=\"true\" role=\"img\" viewBox=\"0 0 512 512\" style=\"height:1em;width:1em;vertical-align:-0.125em;margin-left:auto;margin-right:auto;font-size:inherit;fill:currentColor;overflow:visible;position:relative;\"><path d=\"M244 84L255.1 96L267.1 84.02C300.6 51.37 347 36.51 392.6 44.1C461.5 55.58 512 115.2 512 185.1V190.9C512 232.4 494.8 272.1 464.4 300.4L283.7 469.1C276.2 476.1 266.3 480 256 480C245.7 480 235.8 476.1 228.3 469.1L47.59 300.4C17.23 272.1 0 232.4 0 190.9V185.1C0 115.2 50.52 55.58 119.4 44.1C164.1 36.51 211.4 51.37 244 84C243.1 84 244 84.01 244 84L244 84zM255.1 163.9L210.1 117.1C188.4 96.28 157.6 86.4 127.3 91.44C81.55 99.07 48 138.7 48 185.1V190.9C48 219.1 59.71 246.1 80.34 265.3L256 429.3L431.7 265.3C452.3 246.1 464 219.1 464 190.9V185.1C464 138.7 430.4 99.07 384.7 91.44C354.4 86.4 323.6 96.28 301.9 117.1L255.1 163.9z\"/><\/svg>","<svg aria-hidden=\"true\" role=\"img\" viewBox=\"0 0 512 512\" style=\"height:1em;width:1em;vertical-align:-0.125em;margin-left:auto;margin-right:auto;font-size:inherit;fill:currentColor;overflow:visible;position:relative;\"><path d=\"M244 84L255.1 96L267.1 84.02C300.6 51.37 347 36.51 392.6 44.1C461.5 55.58 512 115.2 512 185.1V190.9C512 232.4 494.8 272.1 464.4 300.4L283.7 469.1C276.2 476.1 266.3 480 256 480C245.7 480 235.8 476.1 228.3 469.1L47.59 300.4C17.23 272.1 0 232.4 0 190.9V185.1C0 115.2 50.52 55.58 119.4 44.1C164.1 36.51 211.4 51.37 244 84C243.1 84 244 84.01 244 84L244 84zM255.1 163.9L210.1 117.1C188.4 96.28 157.6 86.4 127.3 91.44C81.55 99.07 48 138.7 48 185.1V190.9C48 219.1 59.71 246.1 80.34 265.3L256 429.3L431.7 265.3C452.3 246.1 464 219.1 464 190.9V185.1C464 138.7 430.4 99.07 384.7 91.44C354.4 86.4 323.6 96.28 301.9 117.1L255.1 163.9z\"/><\/svg><svg aria-hidden=\"true\" role=\"img\" viewBox=\"0 0 512 512\" style=\"height:1em;width:1em;vertical-align:-0.125em;margin-left:auto;margin-right:auto;font-size:inherit;fill:currentColor;overflow:visible;position:relative;\"><path d=\"M244 84L255.1 96L267.1 84.02C300.6 51.37 347 36.51 392.6 44.1C461.5 55.58 512 115.2 512 185.1V190.9C512 232.4 494.8 272.1 464.4 300.4L283.7 469.1C276.2 476.1 266.3 480 256 480C245.7 480 235.8 476.1 228.3 469.1L47.59 300.4C17.23 272.1 0 232.4 0 190.9V185.1C0 115.2 50.52 55.58 119.4 44.1C164.1 36.51 211.4 51.37 244 84C243.1 84 244 84.01 244 84L244 84zM255.1 163.9L210.1 117.1C188.4 96.28 157.6 86.4 127.3 91.44C81.55 99.07 48 138.7 48 185.1V190.9C48 219.1 59.71 246.1 80.34 265.3L256 429.3L431.7 265.3C452.3 246.1 464 219.1 464 190.9V185.1C464 138.7 430.4 99.07 384.7 91.44C354.4 86.4 323.6 96.28 301.9 117.1L255.1 163.9z\"/><\/svg>","<svg aria-hidden=\"true\" role=\"img\" viewBox=\"0 0 512 512\" style=\"height:1em;width:1em;vertical-align:-0.125em;margin-left:auto;margin-right:auto;font-size:inherit;fill:currentColor;overflow:visible;position:relative;\"><path d=\"M244 84L255.1 96L267.1 84.02C300.6 51.37 347 36.51 392.6 44.1C461.5 55.58 512 115.2 512 185.1V190.9C512 232.4 494.8 272.1 464.4 300.4L283.7 469.1C276.2 476.1 266.3 480 256 480C245.7 480 235.8 476.1 228.3 469.1L47.59 300.4C17.23 272.1 0 232.4 0 190.9V185.1C0 115.2 50.52 55.58 119.4 44.1C164.1 36.51 211.4 51.37 244 84C243.1 84 244 84.01 244 84L244 84zM255.1 163.9L210.1 117.1C188.4 96.28 157.6 86.4 127.3 91.44C81.55 99.07 48 138.7 48 185.1V190.9C48 219.1 59.71 246.1 80.34 265.3L256 429.3L431.7 265.3C452.3 246.1 464 219.1 464 190.9V185.1C464 138.7 430.4 99.07 384.7 91.44C354.4 86.4 323.6 96.28 301.9 117.1L255.1 163.9z\"/><\/svg><svg aria-hidden=\"true\" role=\"img\" viewBox=\"0 0 512 512\" style=\"height:1em;width:1em;vertical-align:-0.125em;margin-left:auto;margin-right:auto;font-size:inherit;fill:currentColor;overflow:visible;position:relative;\"><path d=\"M244 84L255.1 96L267.1 84.02C300.6 51.37 347 36.51 392.6 44.1C461.5 55.58 512 115.2 512 185.1V190.9C512 232.4 494.8 272.1 464.4 300.4L283.7 469.1C276.2 476.1 266.3 480 256 480C245.7 480 235.8 476.1 228.3 469.1L47.59 300.4C17.23 272.1 0 232.4 0 190.9V185.1C0 115.2 50.52 55.58 119.4 44.1C164.1 36.51 211.4 51.37 244 84C243.1 84 244 84.01 244 84L244 84zM255.1 163.9L210.1 117.1C188.4 96.28 157.6 86.4 127.3 91.44C81.55 99.07 48 138.7 48 185.1V190.9C48 219.1 59.71 246.1 80.34 265.3L256 429.3L431.7 265.3C452.3 246.1 464 219.1 464 190.9V185.1C464 138.7 430.4 99.07 384.7 91.44C354.4 86.4 323.6 96.28 301.9 117.1L255.1 163.9z\"/><\/svg><svg aria-hidden=\"true\" role=\"img\" viewBox=\"0 0 512 512\" style=\"height:1em;width:1em;vertical-align:-0.125em;margin-left:auto;margin-right:auto;font-size:inherit;fill:currentColor;overflow:visible;position:relative;\"><path d=\"M244 84L255.1 96L267.1 84.02C300.6 51.37 347 36.51 392.6 44.1C461.5 55.58 512 115.2 512 185.1V190.9C512 232.4 494.8 272.1 464.4 300.4L283.7 469.1C276.2 476.1 266.3 480 256 480C245.7 480 235.8 476.1 228.3 469.1L47.59 300.4C17.23 272.1 0 232.4 0 190.9V185.1C0 115.2 50.52 55.58 119.4 44.1C164.1 36.51 211.4 51.37 244 84C243.1 84 244 84.01 244 84L244 84zM255.1 163.9L210.1 117.1C188.4 96.28 157.6 86.4 127.3 91.44C81.55 99.07 48 138.7 48 185.1V190.9C48 219.1 59.71 246.1 80.34 265.3L256 429.3L431.7 265.3C452.3 246.1 464 219.1 464 190.9V185.1C464 138.7 430.4 99.07 384.7 91.44C354.4 86.4 323.6 96.28 301.9 117.1L255.1 163.9z\"/><\/svg><svg aria-hidden=\"true\" role=\"img\" viewBox=\"0 0 512 512\" style=\"height:1em;width:1em;vertical-align:-0.125em;margin-left:auto;margin-right:auto;font-size:inherit;fill:currentColor;overflow:visible;position:relative;\"><path d=\"M244 84L255.1 96L267.1 84.02C300.6 51.37 347 36.51 392.6 44.1C461.5 55.58 512 115.2 512 185.1V190.9C512 232.4 494.8 272.1 464.4 300.4L283.7 469.1C276.2 476.1 266.3 480 256 480C245.7 480 235.8 476.1 228.3 469.1L47.59 300.4C17.23 272.1 0 232.4 0 190.9V185.1C0 115.2 50.52 55.58 119.4 44.1C164.1 36.51 211.4 51.37 244 84C243.1 84 244 84.01 244 84L244 84zM255.1 163.9L210.1 117.1C188.4 96.28 157.6 86.4 127.3 91.44C81.55 99.07 48 138.7 48 185.1V190.9C48 219.1 59.71 246.1 80.34 265.3L256 429.3L431.7 265.3C452.3 246.1 464 219.1 464 190.9V185.1C464 138.7 430.4 99.07 384.7 91.44C354.4 86.4 323.6 96.28 301.9 117.1L255.1 163.9z\"/><\/svg><svg aria-hidden=\"true\" role=\"img\" viewBox=\"0 0 512 512\" style=\"height:1em;width:1em;vertical-align:-0.125em;margin-left:auto;margin-right:auto;font-size:inherit;fill:currentColor;overflow:visible;position:relative;\"><path d=\"M244 84L255.1 96L267.1 84.02C300.6 51.37 347 36.51 392.6 44.1C461.5 55.58 512 115.2 512 185.1V190.9C512 232.4 494.8 272.1 464.4 300.4L283.7 469.1C276.2 476.1 266.3 480 256 480C245.7 480 235.8 476.1 228.3 469.1L47.59 300.4C17.23 272.1 0 232.4 0 190.9V185.1C0 115.2 50.52 55.58 119.4 44.1C164.1 36.51 211.4 51.37 244 84C243.1 84 244 84.01 244 84L244 84zM255.1 163.9L210.1 117.1C188.4 96.28 157.6 86.4 127.3 91.44C81.55 99.07 48 138.7 48 185.1V190.9C48 219.1 59.71 246.1 80.34 265.3L256 429.3L431.7 265.3C452.3 246.1 464 219.1 464 190.9V185.1C464 138.7 430.4 99.07 384.7 91.44C354.4 86.4 323.6 96.28 301.9 117.1L255.1 163.9z\"/><\/svg>","<svg aria-hidden=\"true\" role=\"img\" viewBox=\"0 0 512 512\" style=\"height:1em;width:1em;vertical-align:-0.125em;margin-left:auto;margin-right:auto;font-size:inherit;fill:currentColor;overflow:visible;position:relative;\"><path d=\"M244 84L255.1 96L267.1 84.02C300.6 51.37 347 36.51 392.6 44.1C461.5 55.58 512 115.2 512 185.1V190.9C512 232.4 494.8 272.1 464.4 300.4L283.7 469.1C276.2 476.1 266.3 480 256 480C245.7 480 235.8 476.1 228.3 469.1L47.59 300.4C17.23 272.1 0 232.4 0 190.9V185.1C0 115.2 50.52 55.58 119.4 44.1C164.1 36.51 211.4 51.37 244 84C243.1 84 244 84.01 244 84L244 84zM255.1 163.9L210.1 117.1C188.4 96.28 157.6 86.4 127.3 91.44C81.55 99.07 48 138.7 48 185.1V190.9C48 219.1 59.71 246.1 80.34 265.3L256 429.3L431.7 265.3C452.3 246.1 464 219.1 464 190.9V185.1C464 138.7 430.4 99.07 384.7 91.44C354.4 86.4 323.6 96.28 301.9 117.1L255.1 163.9z\"/><\/svg><svg aria-hidden=\"true\" role=\"img\" viewBox=\"0 0 512 512\" style=\"height:1em;width:1em;vertical-align:-0.125em;margin-left:auto;margin-right:auto;font-size:inherit;fill:currentColor;overflow:visible;position:relative;\"><path d=\"M244 84L255.1 96L267.1 84.02C300.6 51.37 347 36.51 392.6 44.1C461.5 55.58 512 115.2 512 185.1V190.9C512 232.4 494.8 272.1 464.4 300.4L283.7 469.1C276.2 476.1 266.3 480 256 480C245.7 480 235.8 476.1 228.3 469.1L47.59 300.4C17.23 272.1 0 232.4 0 190.9V185.1C0 115.2 50.52 55.58 119.4 44.1C164.1 36.51 211.4 51.37 244 84C243.1 84 244 84.01 244 84L244 84zM255.1 163.9L210.1 117.1C188.4 96.28 157.6 86.4 127.3 91.44C81.55 99.07 48 138.7 48 185.1V190.9C48 219.1 59.71 246.1 80.34 265.3L256 429.3L431.7 265.3C452.3 246.1 464 219.1 464 190.9V185.1C464 138.7 430.4 99.07 384.7 91.44C354.4 86.4 323.6 96.28 301.9 117.1L255.1 163.9z\"/><\/svg>","<svg aria-hidden=\"true\" role=\"img\" viewBox=\"0 0 512 512\" style=\"height:1em;width:1em;vertical-align:-0.125em;margin-left:auto;margin-right:auto;font-size:inherit;fill:currentColor;overflow:visible;position:relative;\"><path d=\"M244 84L255.1 96L267.1 84.02C300.6 51.37 347 36.51 392.6 44.1C461.5 55.58 512 115.2 512 185.1V190.9C512 232.4 494.8 272.1 464.4 300.4L283.7 469.1C276.2 476.1 266.3 480 256 480C245.7 480 235.8 476.1 228.3 469.1L47.59 300.4C17.23 272.1 0 232.4 0 190.9V185.1C0 115.2 50.52 55.58 119.4 44.1C164.1 36.51 211.4 51.37 244 84C243.1 84 244 84.01 244 84L244 84zM255.1 163.9L210.1 117.1C188.4 96.28 157.6 86.4 127.3 91.44C81.55 99.07 48 138.7 48 185.1V190.9C48 219.1 59.71 246.1 80.34 265.3L256 429.3L431.7 265.3C452.3 246.1 464 219.1 464 190.9V185.1C464 138.7 430.4 99.07 384.7 91.44C354.4 86.4 323.6 96.28 301.9 117.1L255.1 163.9z\"/><\/svg>","<svg aria-hidden=\"true\" role=\"img\" viewBox=\"0 0 512 512\" style=\"height:1em;width:1em;vertical-align:-0.125em;margin-left:auto;margin-right:auto;font-size:inherit;fill:currentColor;overflow:visible;position:relative;\"><path d=\"M244 84L255.1 96L267.1 84.02C300.6 51.37 347 36.51 392.6 44.1C461.5 55.58 512 115.2 512 185.1V190.9C512 232.4 494.8 272.1 464.4 300.4L283.7 469.1C276.2 476.1 266.3 480 256 480C245.7 480 235.8 476.1 228.3 469.1L47.59 300.4C17.23 272.1 0 232.4 0 190.9V185.1C0 115.2 50.52 55.58 119.4 44.1C164.1 36.51 211.4 51.37 244 84C243.1 84 244 84.01 244 84L244 84zM255.1 163.9L210.1 117.1C188.4 96.28 157.6 86.4 127.3 91.44C81.55 99.07 48 138.7 48 185.1V190.9C48 219.1 59.71 246.1 80.34 265.3L256 429.3L431.7 265.3C452.3 246.1 464 219.1 464 190.9V185.1C464 138.7 430.4 99.07 384.7 91.44C354.4 86.4 323.6 96.28 301.9 117.1L255.1 163.9z\"/><\/svg><svg aria-hidden=\"true\" role=\"img\" viewBox=\"0 0 512 512\" style=\"height:1em;width:1em;vertical-align:-0.125em;margin-left:auto;margin-right:auto;font-size:inherit;fill:currentColor;overflow:visible;position:relative;\"><path d=\"M244 84L255.1 96L267.1 84.02C300.6 51.37 347 36.51 392.6 44.1C461.5 55.58 512 115.2 512 185.1V190.9C512 232.4 494.8 272.1 464.4 300.4L283.7 469.1C276.2 476.1 266.3 480 256 480C245.7 480 235.8 476.1 228.3 469.1L47.59 300.4C17.23 272.1 0 232.4 0 190.9V185.1C0 115.2 50.52 55.58 119.4 44.1C164.1 36.51 211.4 51.37 244 84C243.1 84 244 84.01 244 84L244 84zM255.1 163.9L210.1 117.1C188.4 96.28 157.6 86.4 127.3 91.44C81.55 99.07 48 138.7 48 185.1V190.9C48 219.1 59.71 246.1 80.34 265.3L256 429.3L431.7 265.3C452.3 246.1 464 219.1 464 190.9V185.1C464 138.7 430.4 99.07 384.7 91.44C354.4 86.4 323.6 96.28 301.9 117.1L255.1 163.9z\"/><\/svg><svg aria-hidden=\"true\" role=\"img\" viewBox=\"0 0 512 512\" style=\"height:1em;width:1em;vertical-align:-0.125em;margin-left:auto;margin-right:auto;font-size:inherit;fill:currentColor;overflow:visible;position:relative;\"><path d=\"M244 84L255.1 96L267.1 84.02C300.6 51.37 347 36.51 392.6 44.1C461.5 55.58 512 115.2 512 185.1V190.9C512 232.4 494.8 272.1 464.4 300.4L283.7 469.1C276.2 476.1 266.3 480 256 480C245.7 480 235.8 476.1 228.3 469.1L47.59 300.4C17.23 272.1 0 232.4 0 190.9V185.1C0 115.2 50.52 55.58 119.4 44.1C164.1 36.51 211.4 51.37 244 84C243.1 84 244 84.01 244 84L244 84zM255.1 163.9L210.1 117.1C188.4 96.28 157.6 86.4 127.3 91.44C81.55 99.07 48 138.7 48 185.1V190.9C48 219.1 59.71 246.1 80.34 265.3L256 429.3L431.7 265.3C452.3 246.1 464 219.1 464 190.9V185.1C464 138.7 430.4 99.07 384.7 91.44C354.4 86.4 323.6 96.28 301.9 117.1L255.1 163.9z\"/><\/svg>","<svg aria-hidden=\"true\" role=\"img\" viewBox=\"0 0 512 512\" style=\"height:1em;width:1em;vertical-align:-0.125em;margin-left:auto;margin-right:auto;font-size:inherit;fill:currentColor;overflow:visible;position:relative;\"><path d=\"M244 84L255.1 96L267.1 84.02C300.6 51.37 347 36.51 392.6 44.1C461.5 55.58 512 115.2 512 185.1V190.9C512 232.4 494.8 272.1 464.4 300.4L283.7 469.1C276.2 476.1 266.3 480 256 480C245.7 480 235.8 476.1 228.3 469.1L47.59 300.4C17.23 272.1 0 232.4 0 190.9V185.1C0 115.2 50.52 55.58 119.4 44.1C164.1 36.51 211.4 51.37 244 84C243.1 84 244 84.01 244 84L244 84zM255.1 163.9L210.1 117.1C188.4 96.28 157.6 86.4 127.3 91.44C81.55 99.07 48 138.7 48 185.1V190.9C48 219.1 59.71 246.1 80.34 265.3L256 429.3L431.7 265.3C452.3 246.1 464 219.1 464 190.9V185.1C464 138.7 430.4 99.07 384.7 91.44C354.4 86.4 323.6 96.28 301.9 117.1L255.1 163.9z\"/><\/svg>","<svg aria-hidden=\"true\" role=\"img\" viewBox=\"0 0 512 512\" style=\"height:1em;width:1em;vertical-align:-0.125em;margin-left:auto;margin-right:auto;font-size:inherit;fill:currentColor;overflow:visible;position:relative;\"><path d=\"M244 84L255.1 96L267.1 84.02C300.6 51.37 347 36.51 392.6 44.1C461.5 55.58 512 115.2 512 185.1V190.9C512 232.4 494.8 272.1 464.4 300.4L283.7 469.1C276.2 476.1 266.3 480 256 480C245.7 480 235.8 476.1 228.3 469.1L47.59 300.4C17.23 272.1 0 232.4 0 190.9V185.1C0 115.2 50.52 55.58 119.4 44.1C164.1 36.51 211.4 51.37 244 84C243.1 84 244 84.01 244 84L244 84zM255.1 163.9L210.1 117.1C188.4 96.28 157.6 86.4 127.3 91.44C81.55 99.07 48 138.7 48 185.1V190.9C48 219.1 59.71 246.1 80.34 265.3L256 429.3L431.7 265.3C452.3 246.1 464 219.1 464 190.9V185.1C464 138.7 430.4 99.07 384.7 91.44C354.4 86.4 323.6 96.28 301.9 117.1L255.1 163.9z\"/><\/svg><svg aria-hidden=\"true\" role=\"img\" viewBox=\"0 0 512 512\" style=\"height:1em;width:1em;vertical-align:-0.125em;margin-left:auto;margin-right:auto;font-size:inherit;fill:currentColor;overflow:visible;position:relative;\"><path d=\"M244 84L255.1 96L267.1 84.02C300.6 51.37 347 36.51 392.6 44.1C461.5 55.58 512 115.2 512 185.1V190.9C512 232.4 494.8 272.1 464.4 300.4L283.7 469.1C276.2 476.1 266.3 480 256 480C245.7 480 235.8 476.1 228.3 469.1L47.59 300.4C17.23 272.1 0 232.4 0 190.9V185.1C0 115.2 50.52 55.58 119.4 44.1C164.1 36.51 211.4 51.37 244 84C243.1 84 244 84.01 244 84L244 84zM255.1 163.9L210.1 117.1C188.4 96.28 157.6 86.4 127.3 91.44C81.55 99.07 48 138.7 48 185.1V190.9C48 219.1 59.71 246.1 80.34 265.3L256 429.3L431.7 265.3C452.3 246.1 464 219.1 464 190.9V185.1C464 138.7 430.4 99.07 384.7 91.44C354.4 86.4 323.6 96.28 301.9 117.1L255.1 163.9z\"/><\/svg><svg aria-hidden=\"true\" role=\"img\" viewBox=\"0 0 512 512\" style=\"height:1em;width:1em;vertical-align:-0.125em;margin-left:auto;margin-right:auto;font-size:inherit;fill:currentColor;overflow:visible;position:relative;\"><path d=\"M244 84L255.1 96L267.1 84.02C300.6 51.37 347 36.51 392.6 44.1C461.5 55.58 512 115.2 512 185.1V190.9C512 232.4 494.8 272.1 464.4 300.4L283.7 469.1C276.2 476.1 266.3 480 256 480C245.7 480 235.8 476.1 228.3 469.1L47.59 300.4C17.23 272.1 0 232.4 0 190.9V185.1C0 115.2 50.52 55.58 119.4 44.1C164.1 36.51 211.4 51.37 244 84C243.1 84 244 84.01 244 84L244 84zM255.1 163.9L210.1 117.1C188.4 96.28 157.6 86.4 127.3 91.44C81.55 99.07 48 138.7 48 185.1V190.9C48 219.1 59.71 246.1 80.34 265.3L256 429.3L431.7 265.3C452.3 246.1 464 219.1 464 190.9V185.1C464 138.7 430.4 99.07 384.7 91.44C354.4 86.4 323.6 96.28 301.9 117.1L255.1 163.9z\"/><\/svg>","<svg aria-hidden=\"true\" role=\"img\" viewBox=\"0 0 512 512\" style=\"height:1em;width:1em;vertical-align:-0.125em;margin-left:auto;margin-right:auto;font-size:inherit;fill:currentColor;overflow:visible;position:relative;\"><path d=\"M244 84L255.1 96L267.1 84.02C300.6 51.37 347 36.51 392.6 44.1C461.5 55.58 512 115.2 512 185.1V190.9C512 232.4 494.8 272.1 464.4 300.4L283.7 469.1C276.2 476.1 266.3 480 256 480C245.7 480 235.8 476.1 228.3 469.1L47.59 300.4C17.23 272.1 0 232.4 0 190.9V185.1C0 115.2 50.52 55.58 119.4 44.1C164.1 36.51 211.4 51.37 244 84C243.1 84 244 84.01 244 84L244 84zM255.1 163.9L210.1 117.1C188.4 96.28 157.6 86.4 127.3 91.44C81.55 99.07 48 138.7 48 185.1V190.9C48 219.1 59.71 246.1 80.34 265.3L256 429.3L431.7 265.3C452.3 246.1 464 219.1 464 190.9V185.1C464 138.7 430.4 99.07 384.7 91.44C354.4 86.4 323.6 96.28 301.9 117.1L255.1 163.9z\"/><\/svg><svg aria-hidden=\"true\" role=\"img\" viewBox=\"0 0 512 512\" style=\"height:1em;width:1em;vertical-align:-0.125em;margin-left:auto;margin-right:auto;font-size:inherit;fill:currentColor;overflow:visible;position:relative;\"><path d=\"M244 84L255.1 96L267.1 84.02C300.6 51.37 347 36.51 392.6 44.1C461.5 55.58 512 115.2 512 185.1V190.9C512 232.4 494.8 272.1 464.4 300.4L283.7 469.1C276.2 476.1 266.3 480 256 480C245.7 480 235.8 476.1 228.3 469.1L47.59 300.4C17.23 272.1 0 232.4 0 190.9V185.1C0 115.2 50.52 55.58 119.4 44.1C164.1 36.51 211.4 51.37 244 84C243.1 84 244 84.01 244 84L244 84zM255.1 163.9L210.1 117.1C188.4 96.28 157.6 86.4 127.3 91.44C81.55 99.07 48 138.7 48 185.1V190.9C48 219.1 59.71 246.1 80.34 265.3L256 429.3L431.7 265.3C452.3 246.1 464 219.1 464 190.9V185.1C464 138.7 430.4 99.07 384.7 91.44C354.4 86.4 323.6 96.28 301.9 117.1L255.1 163.9z\"/><\/svg><svg aria-hidden=\"true\" role=\"img\" viewBox=\"0 0 512 512\" style=\"height:1em;width:1em;vertical-align:-0.125em;margin-left:auto;margin-right:auto;font-size:inherit;fill:currentColor;overflow:visible;position:relative;\"><path d=\"M244 84L255.1 96L267.1 84.02C300.6 51.37 347 36.51 392.6 44.1C461.5 55.58 512 115.2 512 185.1V190.9C512 232.4 494.8 272.1 464.4 300.4L283.7 469.1C276.2 476.1 266.3 480 256 480C245.7 480 235.8 476.1 228.3 469.1L47.59 300.4C17.23 272.1 0 232.4 0 190.9V185.1C0 115.2 50.52 55.58 119.4 44.1C164.1 36.51 211.4 51.37 244 84C243.1 84 244 84.01 244 84L244 84zM255.1 163.9L210.1 117.1C188.4 96.28 157.6 86.4 127.3 91.44C81.55 99.07 48 138.7 48 185.1V190.9C48 219.1 59.71 246.1 80.34 265.3L256 429.3L431.7 265.3C452.3 246.1 464 219.1 464 190.9V185.1C464 138.7 430.4 99.07 384.7 91.44C354.4 86.4 323.6 96.28 301.9 117.1L255.1 163.9z\"/><\/svg><svg aria-hidden=\"true\" role=\"img\" viewBox=\"0 0 512 512\" style=\"height:1em;width:1em;vertical-align:-0.125em;margin-left:auto;margin-right:auto;font-size:inherit;fill:currentColor;overflow:visible;position:relative;\"><path d=\"M244 84L255.1 96L267.1 84.02C300.6 51.37 347 36.51 392.6 44.1C461.5 55.58 512 115.2 512 185.1V190.9C512 232.4 494.8 272.1 464.4 300.4L283.7 469.1C276.2 476.1 266.3 480 256 480C245.7 480 235.8 476.1 228.3 469.1L47.59 300.4C17.23 272.1 0 232.4 0 190.9V185.1C0 115.2 50.52 55.58 119.4 44.1C164.1 36.51 211.4 51.37 244 84C243.1 84 244 84.01 244 84L244 84zM255.1 163.9L210.1 117.1C188.4 96.28 157.6 86.4 127.3 91.44C81.55 99.07 48 138.7 48 185.1V190.9C48 219.1 59.71 246.1 80.34 265.3L256 429.3L431.7 265.3C452.3 246.1 464 219.1 464 190.9V185.1C464 138.7 430.4 99.07 384.7 91.44C354.4 86.4 323.6 96.28 301.9 117.1L255.1 163.9z\"/><\/svg><svg aria-hidden=\"true\" role=\"img\" viewBox=\"0 0 512 512\" style=\"height:1em;width:1em;vertical-align:-0.125em;margin-left:auto;margin-right:auto;font-size:inherit;fill:currentColor;overflow:visible;position:relative;\"><path d=\"M244 84L255.1 96L267.1 84.02C300.6 51.37 347 36.51 392.6 44.1C461.5 55.58 512 115.2 512 185.1V190.9C512 232.4 494.8 272.1 464.4 300.4L283.7 469.1C276.2 476.1 266.3 480 256 480C245.7 480 235.8 476.1 228.3 469.1L47.59 300.4C17.23 272.1 0 232.4 0 190.9V185.1C0 115.2 50.52 55.58 119.4 44.1C164.1 36.51 211.4 51.37 244 84C243.1 84 244 84.01 244 84L244 84zM255.1 163.9L210.1 117.1C188.4 96.28 157.6 86.4 127.3 91.44C81.55 99.07 48 138.7 48 185.1V190.9C48 219.1 59.71 246.1 80.34 265.3L256 429.3L431.7 265.3C452.3 246.1 464 219.1 464 190.9V185.1C464 138.7 430.4 99.07 384.7 91.44C354.4 86.4 323.6 96.28 301.9 117.1L255.1 163.9z\"/><\/svg>","<svg aria-hidden=\"true\" role=\"img\" viewBox=\"0 0 512 512\" style=\"height:1em;width:1em;vertical-align:-0.125em;margin-left:auto;margin-right:auto;font-size:inherit;fill:currentColor;overflow:visible;position:relative;\"><path d=\"M244 84L255.1 96L267.1 84.02C300.6 51.37 347 36.51 392.6 44.1C461.5 55.58 512 115.2 512 185.1V190.9C512 232.4 494.8 272.1 464.4 300.4L283.7 469.1C276.2 476.1 266.3 480 256 480C245.7 480 235.8 476.1 228.3 469.1L47.59 300.4C17.23 272.1 0 232.4 0 190.9V185.1C0 115.2 50.52 55.58 119.4 44.1C164.1 36.51 211.4 51.37 244 84C243.1 84 244 84.01 244 84L244 84zM255.1 163.9L210.1 117.1C188.4 96.28 157.6 86.4 127.3 91.44C81.55 99.07 48 138.7 48 185.1V190.9C48 219.1 59.71 246.1 80.34 265.3L256 429.3L431.7 265.3C452.3 246.1 464 219.1 464 190.9V185.1C464 138.7 430.4 99.07 384.7 91.44C354.4 86.4 323.6 96.28 301.9 117.1L255.1 163.9z\"/><\/svg><svg aria-hidden=\"true\" role=\"img\" viewBox=\"0 0 512 512\" style=\"height:1em;width:1em;vertical-align:-0.125em;margin-left:auto;margin-right:auto;font-size:inherit;fill:currentColor;overflow:visible;position:relative;\"><path d=\"M244 84L255.1 96L267.1 84.02C300.6 51.37 347 36.51 392.6 44.1C461.5 55.58 512 115.2 512 185.1V190.9C512 232.4 494.8 272.1 464.4 300.4L283.7 469.1C276.2 476.1 266.3 480 256 480C245.7 480 235.8 476.1 228.3 469.1L47.59 300.4C17.23 272.1 0 232.4 0 190.9V185.1C0 115.2 50.52 55.58 119.4 44.1C164.1 36.51 211.4 51.37 244 84C243.1 84 244 84.01 244 84L244 84zM255.1 163.9L210.1 117.1C188.4 96.28 157.6 86.4 127.3 91.44C81.55 99.07 48 138.7 48 185.1V190.9C48 219.1 59.71 246.1 80.34 265.3L256 429.3L431.7 265.3C452.3 246.1 464 219.1 464 190.9V185.1C464 138.7 430.4 99.07 384.7 91.44C354.4 86.4 323.6 96.28 301.9 117.1L255.1 163.9z\"/><\/svg><svg aria-hidden=\"true\" role=\"img\" viewBox=\"0 0 512 512\" style=\"height:1em;width:1em;vertical-align:-0.125em;margin-left:auto;margin-right:auto;font-size:inherit;fill:currentColor;overflow:visible;position:relative;\"><path d=\"M244 84L255.1 96L267.1 84.02C300.6 51.37 347 36.51 392.6 44.1C461.5 55.58 512 115.2 512 185.1V190.9C512 232.4 494.8 272.1 464.4 300.4L283.7 469.1C276.2 476.1 266.3 480 256 480C245.7 480 235.8 476.1 228.3 469.1L47.59 300.4C17.23 272.1 0 232.4 0 190.9V185.1C0 115.2 50.52 55.58 119.4 44.1C164.1 36.51 211.4 51.37 244 84C243.1 84 244 84.01 244 84L244 84zM255.1 163.9L210.1 117.1C188.4 96.28 157.6 86.4 127.3 91.44C81.55 99.07 48 138.7 48 185.1V190.9C48 219.1 59.71 246.1 80.34 265.3L256 429.3L431.7 265.3C452.3 246.1 464 219.1 464 190.9V185.1C464 138.7 430.4 99.07 384.7 91.44C354.4 86.4 323.6 96.28 301.9 117.1L255.1 163.9z\"/><\/svg><svg aria-hidden=\"true\" role=\"img\" viewBox=\"0 0 512 512\" style=\"height:1em;width:1em;vertical-align:-0.125em;margin-left:auto;margin-right:auto;font-size:inherit;fill:currentColor;overflow:visible;position:relative;\"><path d=\"M244 84L255.1 96L267.1 84.02C300.6 51.37 347 36.51 392.6 44.1C461.5 55.58 512 115.2 512 185.1V190.9C512 232.4 494.8 272.1 464.4 300.4L283.7 469.1C276.2 476.1 266.3 480 256 480C245.7 480 235.8 476.1 228.3 469.1L47.59 300.4C17.23 272.1 0 232.4 0 190.9V185.1C0 115.2 50.52 55.58 119.4 44.1C164.1 36.51 211.4 51.37 244 84C243.1 84 244 84.01 244 84L244 84zM255.1 163.9L210.1 117.1C188.4 96.28 157.6 86.4 127.3 91.44C81.55 99.07 48 138.7 48 185.1V190.9C48 219.1 59.71 246.1 80.34 265.3L256 429.3L431.7 265.3C452.3 246.1 464 219.1 464 190.9V185.1C464 138.7 430.4 99.07 384.7 91.44C354.4 86.4 323.6 96.28 301.9 117.1L255.1 163.9z\"/><\/svg>","<svg aria-hidden=\"true\" role=\"img\" viewBox=\"0 0 512 512\" style=\"height:1em;width:1em;vertical-align:-0.125em;margin-left:auto;margin-right:auto;font-size:inherit;fill:currentColor;overflow:visible;position:relative;\"><path d=\"M244 84L255.1 96L267.1 84.02C300.6 51.37 347 36.51 392.6 44.1C461.5 55.58 512 115.2 512 185.1V190.9C512 232.4 494.8 272.1 464.4 300.4L283.7 469.1C276.2 476.1 266.3 480 256 480C245.7 480 235.8 476.1 228.3 469.1L47.59 300.4C17.23 272.1 0 232.4 0 190.9V185.1C0 115.2 50.52 55.58 119.4 44.1C164.1 36.51 211.4 51.37 244 84C243.1 84 244 84.01 244 84L244 84zM255.1 163.9L210.1 117.1C188.4 96.28 157.6 86.4 127.3 91.44C81.55 99.07 48 138.7 48 185.1V190.9C48 219.1 59.71 246.1 80.34 265.3L256 429.3L431.7 265.3C452.3 246.1 464 219.1 464 190.9V185.1C464 138.7 430.4 99.07 384.7 91.44C354.4 86.4 323.6 96.28 301.9 117.1L255.1 163.9z\"/><\/svg><svg aria-hidden=\"true\" role=\"img\" viewBox=\"0 0 512 512\" style=\"height:1em;width:1em;vertical-align:-0.125em;margin-left:auto;margin-right:auto;font-size:inherit;fill:currentColor;overflow:visible;position:relative;\"><path d=\"M244 84L255.1 96L267.1 84.02C300.6 51.37 347 36.51 392.6 44.1C461.5 55.58 512 115.2 512 185.1V190.9C512 232.4 494.8 272.1 464.4 300.4L283.7 469.1C276.2 476.1 266.3 480 256 480C245.7 480 235.8 476.1 228.3 469.1L47.59 300.4C17.23 272.1 0 232.4 0 190.9V185.1C0 115.2 50.52 55.58 119.4 44.1C164.1 36.51 211.4 51.37 244 84C243.1 84 244 84.01 244 84L244 84zM255.1 163.9L210.1 117.1C188.4 96.28 157.6 86.4 127.3 91.44C81.55 99.07 48 138.7 48 185.1V190.9C48 219.1 59.71 246.1 80.34 265.3L256 429.3L431.7 265.3C452.3 246.1 464 219.1 464 190.9V185.1C464 138.7 430.4 99.07 384.7 91.44C354.4 86.4 323.6 96.28 301.9 117.1L255.1 163.9z\"/><\/svg>","<svg aria-hidden=\"true\" role=\"img\" viewBox=\"0 0 512 512\" style=\"height:1em;width:1em;vertical-align:-0.125em;margin-left:auto;margin-right:auto;font-size:inherit;fill:currentColor;overflow:visible;position:relative;\"><path d=\"M244 84L255.1 96L267.1 84.02C300.6 51.37 347 36.51 392.6 44.1C461.5 55.58 512 115.2 512 185.1V190.9C512 232.4 494.8 272.1 464.4 300.4L283.7 469.1C276.2 476.1 266.3 480 256 480C245.7 480 235.8 476.1 228.3 469.1L47.59 300.4C17.23 272.1 0 232.4 0 190.9V185.1C0 115.2 50.52 55.58 119.4 44.1C164.1 36.51 211.4 51.37 244 84C243.1 84 244 84.01 244 84L244 84zM255.1 163.9L210.1 117.1C188.4 96.28 157.6 86.4 127.3 91.44C81.55 99.07 48 138.7 48 185.1V190.9C48 219.1 59.71 246.1 80.34 265.3L256 429.3L431.7 265.3C452.3 246.1 464 219.1 464 190.9V185.1C464 138.7 430.4 99.07 384.7 91.44C354.4 86.4 323.6 96.28 301.9 117.1L255.1 163.9z\"/><\/svg>","<svg aria-hidden=\"true\" role=\"img\" viewBox=\"0 0 512 512\" style=\"height:1em;width:1em;vertical-align:-0.125em;margin-left:auto;margin-right:auto;font-size:inherit;fill:currentColor;overflow:visible;position:relative;\"><path d=\"M244 84L255.1 96L267.1 84.02C300.6 51.37 347 36.51 392.6 44.1C461.5 55.58 512 115.2 512 185.1V190.9C512 232.4 494.8 272.1 464.4 300.4L283.7 469.1C276.2 476.1 266.3 480 256 480C245.7 480 235.8 476.1 228.3 469.1L47.59 300.4C17.23 272.1 0 232.4 0 190.9V185.1C0 115.2 50.52 55.58 119.4 44.1C164.1 36.51 211.4 51.37 244 84C243.1 84 244 84.01 244 84L244 84zM255.1 163.9L210.1 117.1C188.4 96.28 157.6 86.4 127.3 91.44C81.55 99.07 48 138.7 48 185.1V190.9C48 219.1 59.71 246.1 80.34 265.3L256 429.3L431.7 265.3C452.3 246.1 464 219.1 464 190.9V185.1C464 138.7 430.4 99.07 384.7 91.44C354.4 86.4 323.6 96.28 301.9 117.1L255.1 163.9z\"/><\/svg>","<svg aria-hidden=\"true\" role=\"img\" viewBox=\"0 0 512 512\" style=\"height:1em;width:1em;vertical-align:-0.125em;margin-left:auto;margin-right:auto;font-size:inherit;fill:currentColor;overflow:visible;position:relative;\"><path d=\"M244 84L255.1 96L267.1 84.02C300.6 51.37 347 36.51 392.6 44.1C461.5 55.58 512 115.2 512 185.1V190.9C512 232.4 494.8 272.1 464.4 300.4L283.7 469.1C276.2 476.1 266.3 480 256 480C245.7 480 235.8 476.1 228.3 469.1L47.59 300.4C17.23 272.1 0 232.4 0 190.9V185.1C0 115.2 50.52 55.58 119.4 44.1C164.1 36.51 211.4 51.37 244 84C243.1 84 244 84.01 244 84L244 84zM255.1 163.9L210.1 117.1C188.4 96.28 157.6 86.4 127.3 91.44C81.55 99.07 48 138.7 48 185.1V190.9C48 219.1 59.71 246.1 80.34 265.3L256 429.3L431.7 265.3C452.3 246.1 464 219.1 464 190.9V185.1C464 138.7 430.4 99.07 384.7 91.44C354.4 86.4 323.6 96.28 301.9 117.1L255.1 163.9z\"/><\/svg><svg aria-hidden=\"true\" role=\"img\" viewBox=\"0 0 512 512\" style=\"height:1em;width:1em;vertical-align:-0.125em;margin-left:auto;margin-right:auto;font-size:inherit;fill:currentColor;overflow:visible;position:relative;\"><path d=\"M244 84L255.1 96L267.1 84.02C300.6 51.37 347 36.51 392.6 44.1C461.5 55.58 512 115.2 512 185.1V190.9C512 232.4 494.8 272.1 464.4 300.4L283.7 469.1C276.2 476.1 266.3 480 256 480C245.7 480 235.8 476.1 228.3 469.1L47.59 300.4C17.23 272.1 0 232.4 0 190.9V185.1C0 115.2 50.52 55.58 119.4 44.1C164.1 36.51 211.4 51.37 244 84C243.1 84 244 84.01 244 84L244 84zM255.1 163.9L210.1 117.1C188.4 96.28 157.6 86.4 127.3 91.44C81.55 99.07 48 138.7 48 185.1V190.9C48 219.1 59.71 246.1 80.34 265.3L256 429.3L431.7 265.3C452.3 246.1 464 219.1 464 190.9V185.1C464 138.7 430.4 99.07 384.7 91.44C354.4 86.4 323.6 96.28 301.9 117.1L255.1 163.9z\"/><\/svg><svg aria-hidden=\"true\" role=\"img\" viewBox=\"0 0 512 512\" style=\"height:1em;width:1em;vertical-align:-0.125em;margin-left:auto;margin-right:auto;font-size:inherit;fill:currentColor;overflow:visible;position:relative;\"><path d=\"M244 84L255.1 96L267.1 84.02C300.6 51.37 347 36.51 392.6 44.1C461.5 55.58 512 115.2 512 185.1V190.9C512 232.4 494.8 272.1 464.4 300.4L283.7 469.1C276.2 476.1 266.3 480 256 480C245.7 480 235.8 476.1 228.3 469.1L47.59 300.4C17.23 272.1 0 232.4 0 190.9V185.1C0 115.2 50.52 55.58 119.4 44.1C164.1 36.51 211.4 51.37 244 84C243.1 84 244 84.01 244 84L244 84zM255.1 163.9L210.1 117.1C188.4 96.28 157.6 86.4 127.3 91.44C81.55 99.07 48 138.7 48 185.1V190.9C48 219.1 59.71 246.1 80.34 265.3L256 429.3L431.7 265.3C452.3 246.1 464 219.1 464 190.9V185.1C464 138.7 430.4 99.07 384.7 91.44C354.4 86.4 323.6 96.28 301.9 117.1L255.1 163.9z\"/><\/svg>","<svg aria-hidden=\"true\" role=\"img\" viewBox=\"0 0 512 512\" style=\"height:1em;width:1em;vertical-align:-0.125em;margin-left:auto;margin-right:auto;font-size:inherit;fill:currentColor;overflow:visible;position:relative;\"><path d=\"M244 84L255.1 96L267.1 84.02C300.6 51.37 347 36.51 392.6 44.1C461.5 55.58 512 115.2 512 185.1V190.9C512 232.4 494.8 272.1 464.4 300.4L283.7 469.1C276.2 476.1 266.3 480 256 480C245.7 480 235.8 476.1 228.3 469.1L47.59 300.4C17.23 272.1 0 232.4 0 190.9V185.1C0 115.2 50.52 55.58 119.4 44.1C164.1 36.51 211.4 51.37 244 84C243.1 84 244 84.01 244 84L244 84zM255.1 163.9L210.1 117.1C188.4 96.28 157.6 86.4 127.3 91.44C81.55 99.07 48 138.7 48 185.1V190.9C48 219.1 59.71 246.1 80.34 265.3L256 429.3L431.7 265.3C452.3 246.1 464 219.1 464 190.9V185.1C464 138.7 430.4 99.07 384.7 91.44C354.4 86.4 323.6 96.28 301.9 117.1L255.1 163.9z\"/><\/svg><svg aria-hidden=\"true\" role=\"img\" viewBox=\"0 0 512 512\" style=\"height:1em;width:1em;vertical-align:-0.125em;margin-left:auto;margin-right:auto;font-size:inherit;fill:currentColor;overflow:visible;position:relative;\"><path d=\"M244 84L255.1 96L267.1 84.02C300.6 51.37 347 36.51 392.6 44.1C461.5 55.58 512 115.2 512 185.1V190.9C512 232.4 494.8 272.1 464.4 300.4L283.7 469.1C276.2 476.1 266.3 480 256 480C245.7 480 235.8 476.1 228.3 469.1L47.59 300.4C17.23 272.1 0 232.4 0 190.9V185.1C0 115.2 50.52 55.58 119.4 44.1C164.1 36.51 211.4 51.37 244 84C243.1 84 244 84.01 244 84L244 84zM255.1 163.9L210.1 117.1C188.4 96.28 157.6 86.4 127.3 91.44C81.55 99.07 48 138.7 48 185.1V190.9C48 219.1 59.71 246.1 80.34 265.3L256 429.3L431.7 265.3C452.3 246.1 464 219.1 464 190.9V185.1C464 138.7 430.4 99.07 384.7 91.44C354.4 86.4 323.6 96.28 301.9 117.1L255.1 163.9z\"/><\/svg><svg aria-hidden=\"true\" role=\"img\" viewBox=\"0 0 512 512\" style=\"height:1em;width:1em;vertical-align:-0.125em;margin-left:auto;margin-right:auto;font-size:inherit;fill:currentColor;overflow:visible;position:relative;\"><path d=\"M244 84L255.1 96L267.1 84.02C300.6 51.37 347 36.51 392.6 44.1C461.5 55.58 512 115.2 512 185.1V190.9C512 232.4 494.8 272.1 464.4 300.4L283.7 469.1C276.2 476.1 266.3 480 256 480C245.7 480 235.8 476.1 228.3 469.1L47.59 300.4C17.23 272.1 0 232.4 0 190.9V185.1C0 115.2 50.52 55.58 119.4 44.1C164.1 36.51 211.4 51.37 244 84C243.1 84 244 84.01 244 84L244 84zM255.1 163.9L210.1 117.1C188.4 96.28 157.6 86.4 127.3 91.44C81.55 99.07 48 138.7 48 185.1V190.9C48 219.1 59.71 246.1 80.34 265.3L256 429.3L431.7 265.3C452.3 246.1 464 219.1 464 190.9V185.1C464 138.7 430.4 99.07 384.7 91.44C354.4 86.4 323.6 96.28 301.9 117.1L255.1 163.9z\"/><\/svg><svg aria-hidden=\"true\" role=\"img\" viewBox=\"0 0 512 512\" style=\"height:1em;width:1em;vertical-align:-0.125em;margin-left:auto;margin-right:auto;font-size:inherit;fill:currentColor;overflow:visible;position:relative;\"><path d=\"M244 84L255.1 96L267.1 84.02C300.6 51.37 347 36.51 392.6 44.1C461.5 55.58 512 115.2 512 185.1V190.9C512 232.4 494.8 272.1 464.4 300.4L283.7 469.1C276.2 476.1 266.3 480 256 480C245.7 480 235.8 476.1 228.3 469.1L47.59 300.4C17.23 272.1 0 232.4 0 190.9V185.1C0 115.2 50.52 55.58 119.4 44.1C164.1 36.51 211.4 51.37 244 84C243.1 84 244 84.01 244 84L244 84zM255.1 163.9L210.1 117.1C188.4 96.28 157.6 86.4 127.3 91.44C81.55 99.07 48 138.7 48 185.1V190.9C48 219.1 59.71 246.1 80.34 265.3L256 429.3L431.7 265.3C452.3 246.1 464 219.1 464 190.9V185.1C464 138.7 430.4 99.07 384.7 91.44C354.4 86.4 323.6 96.28 301.9 117.1L255.1 163.9z\"/><\/svg>","<svg aria-hidden=\"true\" role=\"img\" viewBox=\"0 0 512 512\" style=\"height:1em;width:1em;vertical-align:-0.125em;margin-left:auto;margin-right:auto;font-size:inherit;fill:currentColor;overflow:visible;position:relative;\"><path d=\"M244 84L255.1 96L267.1 84.02C300.6 51.37 347 36.51 392.6 44.1C461.5 55.58 512 115.2 512 185.1V190.9C512 232.4 494.8 272.1 464.4 300.4L283.7 469.1C276.2 476.1 266.3 480 256 480C245.7 480 235.8 476.1 228.3 469.1L47.59 300.4C17.23 272.1 0 232.4 0 190.9V185.1C0 115.2 50.52 55.58 119.4 44.1C164.1 36.51 211.4 51.37 244 84C243.1 84 244 84.01 244 84L244 84zM255.1 163.9L210.1 117.1C188.4 96.28 157.6 86.4 127.3 91.44C81.55 99.07 48 138.7 48 185.1V190.9C48 219.1 59.71 246.1 80.34 265.3L256 429.3L431.7 265.3C452.3 246.1 464 219.1 464 190.9V185.1C464 138.7 430.4 99.07 384.7 91.44C354.4 86.4 323.6 96.28 301.9 117.1L255.1 163.9z\"/><\/svg><svg aria-hidden=\"true\" role=\"img\" viewBox=\"0 0 512 512\" style=\"height:1em;width:1em;vertical-align:-0.125em;margin-left:auto;margin-right:auto;font-size:inherit;fill:currentColor;overflow:visible;position:relative;\"><path d=\"M244 84L255.1 96L267.1 84.02C300.6 51.37 347 36.51 392.6 44.1C461.5 55.58 512 115.2 512 185.1V190.9C512 232.4 494.8 272.1 464.4 300.4L283.7 469.1C276.2 476.1 266.3 480 256 480C245.7 480 235.8 476.1 228.3 469.1L47.59 300.4C17.23 272.1 0 232.4 0 190.9V185.1C0 115.2 50.52 55.58 119.4 44.1C164.1 36.51 211.4 51.37 244 84C243.1 84 244 84.01 244 84L244 84zM255.1 163.9L210.1 117.1C188.4 96.28 157.6 86.4 127.3 91.44C81.55 99.07 48 138.7 48 185.1V190.9C48 219.1 59.71 246.1 80.34 265.3L256 429.3L431.7 265.3C452.3 246.1 464 219.1 464 190.9V185.1C464 138.7 430.4 99.07 384.7 91.44C354.4 86.4 323.6 96.28 301.9 117.1L255.1 163.9z\"/><\/svg>","<svg aria-hidden=\"true\" role=\"img\" viewBox=\"0 0 512 512\" style=\"height:1em;width:1em;vertical-align:-0.125em;margin-left:auto;margin-right:auto;font-size:inherit;fill:currentColor;overflow:visible;position:relative;\"><path d=\"M244 84L255.1 96L267.1 84.02C300.6 51.37 347 36.51 392.6 44.1C461.5 55.58 512 115.2 512 185.1V190.9C512 232.4 494.8 272.1 464.4 300.4L283.7 469.1C276.2 476.1 266.3 480 256 480C245.7 480 235.8 476.1 228.3 469.1L47.59 300.4C17.23 272.1 0 232.4 0 190.9V185.1C0 115.2 50.52 55.58 119.4 44.1C164.1 36.51 211.4 51.37 244 84C243.1 84 244 84.01 244 84L244 84zM255.1 163.9L210.1 117.1C188.4 96.28 157.6 86.4 127.3 91.44C81.55 99.07 48 138.7 48 185.1V190.9C48 219.1 59.71 246.1 80.34 265.3L256 429.3L431.7 265.3C452.3 246.1 464 219.1 464 190.9V185.1C464 138.7 430.4 99.07 384.7 91.44C354.4 86.4 323.6 96.28 301.9 117.1L255.1 163.9z\"/><\/svg>","<svg aria-hidden=\"true\" role=\"img\" viewBox=\"0 0 512 512\" style=\"height:1em;width:1em;vertical-align:-0.125em;margin-left:auto;margin-right:auto;font-size:inherit;fill:currentColor;overflow:visible;position:relative;\"><path d=\"M244 84L255.1 96L267.1 84.02C300.6 51.37 347 36.51 392.6 44.1C461.5 55.58 512 115.2 512 185.1V190.9C512 232.4 494.8 272.1 464.4 300.4L283.7 469.1C276.2 476.1 266.3 480 256 480C245.7 480 235.8 476.1 228.3 469.1L47.59 300.4C17.23 272.1 0 232.4 0 190.9V185.1C0 115.2 50.52 55.58 119.4 44.1C164.1 36.51 211.4 51.37 244 84C243.1 84 244 84.01 244 84L244 84zM255.1 163.9L210.1 117.1C188.4 96.28 157.6 86.4 127.3 91.44C81.55 99.07 48 138.7 48 185.1V190.9C48 219.1 59.71 246.1 80.34 265.3L256 429.3L431.7 265.3C452.3 246.1 464 219.1 464 190.9V185.1C464 138.7 430.4 99.07 384.7 91.44C354.4 86.4 323.6 96.28 301.9 117.1L255.1 163.9z\"/><\/svg><svg aria-hidden=\"true\" role=\"img\" viewBox=\"0 0 512 512\" style=\"height:1em;width:1em;vertical-align:-0.125em;margin-left:auto;margin-right:auto;font-size:inherit;fill:currentColor;overflow:visible;position:relative;\"><path d=\"M244 84L255.1 96L267.1 84.02C300.6 51.37 347 36.51 392.6 44.1C461.5 55.58 512 115.2 512 185.1V190.9C512 232.4 494.8 272.1 464.4 300.4L283.7 469.1C276.2 476.1 266.3 480 256 480C245.7 480 235.8 476.1 228.3 469.1L47.59 300.4C17.23 272.1 0 232.4 0 190.9V185.1C0 115.2 50.52 55.58 119.4 44.1C164.1 36.51 211.4 51.37 244 84C243.1 84 244 84.01 244 84L244 84zM255.1 163.9L210.1 117.1C188.4 96.28 157.6 86.4 127.3 91.44C81.55 99.07 48 138.7 48 185.1V190.9C48 219.1 59.71 246.1 80.34 265.3L256 429.3L431.7 265.3C452.3 246.1 464 219.1 464 190.9V185.1C464 138.7 430.4 99.07 384.7 91.44C354.4 86.4 323.6 96.28 301.9 117.1L255.1 163.9z\"/><\/svg><svg aria-hidden=\"true\" role=\"img\" viewBox=\"0 0 512 512\" style=\"height:1em;width:1em;vertical-align:-0.125em;margin-left:auto;margin-right:auto;font-size:inherit;fill:currentColor;overflow:visible;position:relative;\"><path d=\"M244 84L255.1 96L267.1 84.02C300.6 51.37 347 36.51 392.6 44.1C461.5 55.58 512 115.2 512 185.1V190.9C512 232.4 494.8 272.1 464.4 300.4L283.7 469.1C276.2 476.1 266.3 480 256 480C245.7 480 235.8 476.1 228.3 469.1L47.59 300.4C17.23 272.1 0 232.4 0 190.9V185.1C0 115.2 50.52 55.58 119.4 44.1C164.1 36.51 211.4 51.37 244 84C243.1 84 244 84.01 244 84L244 84zM255.1 163.9L210.1 117.1C188.4 96.28 157.6 86.4 127.3 91.44C81.55 99.07 48 138.7 48 185.1V190.9C48 219.1 59.71 246.1 80.34 265.3L256 429.3L431.7 265.3C452.3 246.1 464 219.1 464 190.9V185.1C464 138.7 430.4 99.07 384.7 91.44C354.4 86.4 323.6 96.28 301.9 117.1L255.1 163.9z\"/><\/svg>","<svg aria-hidden=\"true\" role=\"img\" viewBox=\"0 0 512 512\" style=\"height:1em;width:1em;vertical-align:-0.125em;margin-left:auto;margin-right:auto;font-size:inherit;fill:currentColor;overflow:visible;position:relative;\"><path d=\"M244 84L255.1 96L267.1 84.02C300.6 51.37 347 36.51 392.6 44.1C461.5 55.58 512 115.2 512 185.1V190.9C512 232.4 494.8 272.1 464.4 300.4L283.7 469.1C276.2 476.1 266.3 480 256 480C245.7 480 235.8 476.1 228.3 469.1L47.59 300.4C17.23 272.1 0 232.4 0 190.9V185.1C0 115.2 50.52 55.58 119.4 44.1C164.1 36.51 211.4 51.37 244 84C243.1 84 244 84.01 244 84L244 84zM255.1 163.9L210.1 117.1C188.4 96.28 157.6 86.4 127.3 91.44C81.55 99.07 48 138.7 48 185.1V190.9C48 219.1 59.71 246.1 80.34 265.3L256 429.3L431.7 265.3C452.3 246.1 464 219.1 464 190.9V185.1C464 138.7 430.4 99.07 384.7 91.44C354.4 86.4 323.6 96.28 301.9 117.1L255.1 163.9z\"/><\/svg><svg aria-hidden=\"true\" role=\"img\" viewBox=\"0 0 512 512\" style=\"height:1em;width:1em;vertical-align:-0.125em;margin-left:auto;margin-right:auto;font-size:inherit;fill:currentColor;overflow:visible;position:relative;\"><path d=\"M244 84L255.1 96L267.1 84.02C300.6 51.37 347 36.51 392.6 44.1C461.5 55.58 512 115.2 512 185.1V190.9C512 232.4 494.8 272.1 464.4 300.4L283.7 469.1C276.2 476.1 266.3 480 256 480C245.7 480 235.8 476.1 228.3 469.1L47.59 300.4C17.23 272.1 0 232.4 0 190.9V185.1C0 115.2 50.52 55.58 119.4 44.1C164.1 36.51 211.4 51.37 244 84C243.1 84 244 84.01 244 84L244 84zM255.1 163.9L210.1 117.1C188.4 96.28 157.6 86.4 127.3 91.44C81.55 99.07 48 138.7 48 185.1V190.9C48 219.1 59.71 246.1 80.34 265.3L256 429.3L431.7 265.3C452.3 246.1 464 219.1 464 190.9V185.1C464 138.7 430.4 99.07 384.7 91.44C354.4 86.4 323.6 96.28 301.9 117.1L255.1 163.9z\"/><\/svg>","<svg aria-hidden=\"true\" role=\"img\" viewBox=\"0 0 512 512\" style=\"height:1em;width:1em;vertical-align:-0.125em;margin-left:auto;margin-right:auto;font-size:inherit;fill:currentColor;overflow:visible;position:relative;\"><path d=\"M244 84L255.1 96L267.1 84.02C300.6 51.37 347 36.51 392.6 44.1C461.5 55.58 512 115.2 512 185.1V190.9C512 232.4 494.8 272.1 464.4 300.4L283.7 469.1C276.2 476.1 266.3 480 256 480C245.7 480 235.8 476.1 228.3 469.1L47.59 300.4C17.23 272.1 0 232.4 0 190.9V185.1C0 115.2 50.52 55.58 119.4 44.1C164.1 36.51 211.4 51.37 244 84C243.1 84 244 84.01 244 84L244 84zM255.1 163.9L210.1 117.1C188.4 96.28 157.6 86.4 127.3 91.44C81.55 99.07 48 138.7 48 185.1V190.9C48 219.1 59.71 246.1 80.34 265.3L256 429.3L431.7 265.3C452.3 246.1 464 219.1 464 190.9V185.1C464 138.7 430.4 99.07 384.7 91.44C354.4 86.4 323.6 96.28 301.9 117.1L255.1 163.9z\"/><\/svg><svg aria-hidden=\"true\" role=\"img\" viewBox=\"0 0 512 512\" style=\"height:1em;width:1em;vertical-align:-0.125em;margin-left:auto;margin-right:auto;font-size:inherit;fill:currentColor;overflow:visible;position:relative;\"><path d=\"M244 84L255.1 96L267.1 84.02C300.6 51.37 347 36.51 392.6 44.1C461.5 55.58 512 115.2 512 185.1V190.9C512 232.4 494.8 272.1 464.4 300.4L283.7 469.1C276.2 476.1 266.3 480 256 480C245.7 480 235.8 476.1 228.3 469.1L47.59 300.4C17.23 272.1 0 232.4 0 190.9V185.1C0 115.2 50.52 55.58 119.4 44.1C164.1 36.51 211.4 51.37 244 84C243.1 84 244 84.01 244 84L244 84zM255.1 163.9L210.1 117.1C188.4 96.28 157.6 86.4 127.3 91.44C81.55 99.07 48 138.7 48 185.1V190.9C48 219.1 59.71 246.1 80.34 265.3L256 429.3L431.7 265.3C452.3 246.1 464 219.1 464 190.9V185.1C464 138.7 430.4 99.07 384.7 91.44C354.4 86.4 323.6 96.28 301.9 117.1L255.1 163.9z\"/><\/svg><svg aria-hidden=\"true\" role=\"img\" viewBox=\"0 0 512 512\" style=\"height:1em;width:1em;vertical-align:-0.125em;margin-left:auto;margin-right:auto;font-size:inherit;fill:currentColor;overflow:visible;position:relative;\"><path d=\"M244 84L255.1 96L267.1 84.02C300.6 51.37 347 36.51 392.6 44.1C461.5 55.58 512 115.2 512 185.1V190.9C512 232.4 494.8 272.1 464.4 300.4L283.7 469.1C276.2 476.1 266.3 480 256 480C245.7 480 235.8 476.1 228.3 469.1L47.59 300.4C17.23 272.1 0 232.4 0 190.9V185.1C0 115.2 50.52 55.58 119.4 44.1C164.1 36.51 211.4 51.37 244 84C243.1 84 244 84.01 244 84L244 84zM255.1 163.9L210.1 117.1C188.4 96.28 157.6 86.4 127.3 91.44C81.55 99.07 48 138.7 48 185.1V190.9C48 219.1 59.71 246.1 80.34 265.3L256 429.3L431.7 265.3C452.3 246.1 464 219.1 464 190.9V185.1C464 138.7 430.4 99.07 384.7 91.44C354.4 86.4 323.6 96.28 301.9 117.1L255.1 163.9z\"/><\/svg><svg aria-hidden=\"true\" role=\"img\" viewBox=\"0 0 512 512\" style=\"height:1em;width:1em;vertical-align:-0.125em;margin-left:auto;margin-right:auto;font-size:inherit;fill:currentColor;overflow:visible;position:relative;\"><path d=\"M244 84L255.1 96L267.1 84.02C300.6 51.37 347 36.51 392.6 44.1C461.5 55.58 512 115.2 512 185.1V190.9C512 232.4 494.8 272.1 464.4 300.4L283.7 469.1C276.2 476.1 266.3 480 256 480C245.7 480 235.8 476.1 228.3 469.1L47.59 300.4C17.23 272.1 0 232.4 0 190.9V185.1C0 115.2 50.52 55.58 119.4 44.1C164.1 36.51 211.4 51.37 244 84C243.1 84 244 84.01 244 84L244 84zM255.1 163.9L210.1 117.1C188.4 96.28 157.6 86.4 127.3 91.44C81.55 99.07 48 138.7 48 185.1V190.9C48 219.1 59.71 246.1 80.34 265.3L256 429.3L431.7 265.3C452.3 246.1 464 219.1 464 190.9V185.1C464 138.7 430.4 99.07 384.7 91.44C354.4 86.4 323.6 96.28 301.9 117.1L255.1 163.9z\"/><\/svg>","<svg aria-hidden=\"true\" role=\"img\" viewBox=\"0 0 512 512\" style=\"height:1em;width:1em;vertical-align:-0.125em;margin-left:auto;margin-right:auto;font-size:inherit;fill:currentColor;overflow:visible;position:relative;\"><path d=\"M244 84L255.1 96L267.1 84.02C300.6 51.37 347 36.51 392.6 44.1C461.5 55.58 512 115.2 512 185.1V190.9C512 232.4 494.8 272.1 464.4 300.4L283.7 469.1C276.2 476.1 266.3 480 256 480C245.7 480 235.8 476.1 228.3 469.1L47.59 300.4C17.23 272.1 0 232.4 0 190.9V185.1C0 115.2 50.52 55.58 119.4 44.1C164.1 36.51 211.4 51.37 244 84C243.1 84 244 84.01 244 84L244 84zM255.1 163.9L210.1 117.1C188.4 96.28 157.6 86.4 127.3 91.44C81.55 99.07 48 138.7 48 185.1V190.9C48 219.1 59.71 246.1 80.34 265.3L256 429.3L431.7 265.3C452.3 246.1 464 219.1 464 190.9V185.1C464 138.7 430.4 99.07 384.7 91.44C354.4 86.4 323.6 96.28 301.9 117.1L255.1 163.9z\"/><\/svg><svg aria-hidden=\"true\" role=\"img\" viewBox=\"0 0 512 512\" style=\"height:1em;width:1em;vertical-align:-0.125em;margin-left:auto;margin-right:auto;font-size:inherit;fill:currentColor;overflow:visible;position:relative;\"><path d=\"M244 84L255.1 96L267.1 84.02C300.6 51.37 347 36.51 392.6 44.1C461.5 55.58 512 115.2 512 185.1V190.9C512 232.4 494.8 272.1 464.4 300.4L283.7 469.1C276.2 476.1 266.3 480 256 480C245.7 480 235.8 476.1 228.3 469.1L47.59 300.4C17.23 272.1 0 232.4 0 190.9V185.1C0 115.2 50.52 55.58 119.4 44.1C164.1 36.51 211.4 51.37 244 84C243.1 84 244 84.01 244 84L244 84zM255.1 163.9L210.1 117.1C188.4 96.28 157.6 86.4 127.3 91.44C81.55 99.07 48 138.7 48 185.1V190.9C48 219.1 59.71 246.1 80.34 265.3L256 429.3L431.7 265.3C452.3 246.1 464 219.1 464 190.9V185.1C464 138.7 430.4 99.07 384.7 91.44C354.4 86.4 323.6 96.28 301.9 117.1L255.1 163.9z\"/><\/svg>","<svg aria-hidden=\"true\" role=\"img\" viewBox=\"0 0 512 512\" style=\"height:1em;width:1em;vertical-align:-0.125em;margin-left:auto;margin-right:auto;font-size:inherit;fill:currentColor;overflow:visible;position:relative;\"><path d=\"M244 84L255.1 96L267.1 84.02C300.6 51.37 347 36.51 392.6 44.1C461.5 55.58 512 115.2 512 185.1V190.9C512 232.4 494.8 272.1 464.4 300.4L283.7 469.1C276.2 476.1 266.3 480 256 480C245.7 480 235.8 476.1 228.3 469.1L47.59 300.4C17.23 272.1 0 232.4 0 190.9V185.1C0 115.2 50.52 55.58 119.4 44.1C164.1 36.51 211.4 51.37 244 84C243.1 84 244 84.01 244 84L244 84zM255.1 163.9L210.1 117.1C188.4 96.28 157.6 86.4 127.3 91.44C81.55 99.07 48 138.7 48 185.1V190.9C48 219.1 59.71 246.1 80.34 265.3L256 429.3L431.7 265.3C452.3 246.1 464 219.1 464 190.9V185.1C464 138.7 430.4 99.07 384.7 91.44C354.4 86.4 323.6 96.28 301.9 117.1L255.1 163.9z\"/><\/svg><svg aria-hidden=\"true\" role=\"img\" viewBox=\"0 0 512 512\" style=\"height:1em;width:1em;vertical-align:-0.125em;margin-left:auto;margin-right:auto;font-size:inherit;fill:currentColor;overflow:visible;position:relative;\"><path d=\"M244 84L255.1 96L267.1 84.02C300.6 51.37 347 36.51 392.6 44.1C461.5 55.58 512 115.2 512 185.1V190.9C512 232.4 494.8 272.1 464.4 300.4L283.7 469.1C276.2 476.1 266.3 480 256 480C245.7 480 235.8 476.1 228.3 469.1L47.59 300.4C17.23 272.1 0 232.4 0 190.9V185.1C0 115.2 50.52 55.58 119.4 44.1C164.1 36.51 211.4 51.37 244 84C243.1 84 244 84.01 244 84L244 84zM255.1 163.9L210.1 117.1C188.4 96.28 157.6 86.4 127.3 91.44C81.55 99.07 48 138.7 48 185.1V190.9C48 219.1 59.71 246.1 80.34 265.3L256 429.3L431.7 265.3C452.3 246.1 464 219.1 464 190.9V185.1C464 138.7 430.4 99.07 384.7 91.44C354.4 86.4 323.6 96.28 301.9 117.1L255.1 163.9z\"/><\/svg><svg aria-hidden=\"true\" role=\"img\" viewBox=\"0 0 512 512\" style=\"height:1em;width:1em;vertical-align:-0.125em;margin-left:auto;margin-right:auto;font-size:inherit;fill:currentColor;overflow:visible;position:relative;\"><path d=\"M244 84L255.1 96L267.1 84.02C300.6 51.37 347 36.51 392.6 44.1C461.5 55.58 512 115.2 512 185.1V190.9C512 232.4 494.8 272.1 464.4 300.4L283.7 469.1C276.2 476.1 266.3 480 256 480C245.7 480 235.8 476.1 228.3 469.1L47.59 300.4C17.23 272.1 0 232.4 0 190.9V185.1C0 115.2 50.52 55.58 119.4 44.1C164.1 36.51 211.4 51.37 244 84C243.1 84 244 84.01 244 84L244 84zM255.1 163.9L210.1 117.1C188.4 96.28 157.6 86.4 127.3 91.44C81.55 99.07 48 138.7 48 185.1V190.9C48 219.1 59.71 246.1 80.34 265.3L256 429.3L431.7 265.3C452.3 246.1 464 219.1 464 190.9V185.1C464 138.7 430.4 99.07 384.7 91.44C354.4 86.4 323.6 96.28 301.9 117.1L255.1 163.9z\"/><\/svg><svg aria-hidden=\"true\" role=\"img\" viewBox=\"0 0 512 512\" style=\"height:1em;width:1em;vertical-align:-0.125em;margin-left:auto;margin-right:auto;font-size:inherit;fill:currentColor;overflow:visible;position:relative;\"><path d=\"M244 84L255.1 96L267.1 84.02C300.6 51.37 347 36.51 392.6 44.1C461.5 55.58 512 115.2 512 185.1V190.9C512 232.4 494.8 272.1 464.4 300.4L283.7 469.1C276.2 476.1 266.3 480 256 480C245.7 480 235.8 476.1 228.3 469.1L47.59 300.4C17.23 272.1 0 232.4 0 190.9V185.1C0 115.2 50.52 55.58 119.4 44.1C164.1 36.51 211.4 51.37 244 84C243.1 84 244 84.01 244 84L244 84zM255.1 163.9L210.1 117.1C188.4 96.28 157.6 86.4 127.3 91.44C81.55 99.07 48 138.7 48 185.1V190.9C48 219.1 59.71 246.1 80.34 265.3L256 429.3L431.7 265.3C452.3 246.1 464 219.1 464 190.9V185.1C464 138.7 430.4 99.07 384.7 91.44C354.4 86.4 323.6 96.28 301.9 117.1L255.1 163.9z\"/><\/svg>","<svg aria-hidden=\"true\" role=\"img\" viewBox=\"0 0 512 512\" style=\"height:1em;width:1em;vertical-align:-0.125em;margin-left:auto;margin-right:auto;font-size:inherit;fill:currentColor;overflow:visible;position:relative;\"><path d=\"M244 84L255.1 96L267.1 84.02C300.6 51.37 347 36.51 392.6 44.1C461.5 55.58 512 115.2 512 185.1V190.9C512 232.4 494.8 272.1 464.4 300.4L283.7 469.1C276.2 476.1 266.3 480 256 480C245.7 480 235.8 476.1 228.3 469.1L47.59 300.4C17.23 272.1 0 232.4 0 190.9V185.1C0 115.2 50.52 55.58 119.4 44.1C164.1 36.51 211.4 51.37 244 84C243.1 84 244 84.01 244 84L244 84zM255.1 163.9L210.1 117.1C188.4 96.28 157.6 86.4 127.3 91.44C81.55 99.07 48 138.7 48 185.1V190.9C48 219.1 59.71 246.1 80.34 265.3L256 429.3L431.7 265.3C452.3 246.1 464 219.1 464 190.9V185.1C464 138.7 430.4 99.07 384.7 91.44C354.4 86.4 323.6 96.28 301.9 117.1L255.1 163.9z\"/><\/svg><svg aria-hidden=\"true\" role=\"img\" viewBox=\"0 0 512 512\" style=\"height:1em;width:1em;vertical-align:-0.125em;margin-left:auto;margin-right:auto;font-size:inherit;fill:currentColor;overflow:visible;position:relative;\"><path d=\"M244 84L255.1 96L267.1 84.02C300.6 51.37 347 36.51 392.6 44.1C461.5 55.58 512 115.2 512 185.1V190.9C512 232.4 494.8 272.1 464.4 300.4L283.7 469.1C276.2 476.1 266.3 480 256 480C245.7 480 235.8 476.1 228.3 469.1L47.59 300.4C17.23 272.1 0 232.4 0 190.9V185.1C0 115.2 50.52 55.58 119.4 44.1C164.1 36.51 211.4 51.37 244 84C243.1 84 244 84.01 244 84L244 84zM255.1 163.9L210.1 117.1C188.4 96.28 157.6 86.4 127.3 91.44C81.55 99.07 48 138.7 48 185.1V190.9C48 219.1 59.71 246.1 80.34 265.3L256 429.3L431.7 265.3C452.3 246.1 464 219.1 464 190.9V185.1C464 138.7 430.4 99.07 384.7 91.44C354.4 86.4 323.6 96.28 301.9 117.1L255.1 163.9z\"/><\/svg><svg aria-hidden=\"true\" role=\"img\" viewBox=\"0 0 512 512\" style=\"height:1em;width:1em;vertical-align:-0.125em;margin-left:auto;margin-right:auto;font-size:inherit;fill:currentColor;overflow:visible;position:relative;\"><path d=\"M244 84L255.1 96L267.1 84.02C300.6 51.37 347 36.51 392.6 44.1C461.5 55.58 512 115.2 512 185.1V190.9C512 232.4 494.8 272.1 464.4 300.4L283.7 469.1C276.2 476.1 266.3 480 256 480C245.7 480 235.8 476.1 228.3 469.1L47.59 300.4C17.23 272.1 0 232.4 0 190.9V185.1C0 115.2 50.52 55.58 119.4 44.1C164.1 36.51 211.4 51.37 244 84C243.1 84 244 84.01 244 84L244 84zM255.1 163.9L210.1 117.1C188.4 96.28 157.6 86.4 127.3 91.44C81.55 99.07 48 138.7 48 185.1V190.9C48 219.1 59.71 246.1 80.34 265.3L256 429.3L431.7 265.3C452.3 246.1 464 219.1 464 190.9V185.1C464 138.7 430.4 99.07 384.7 91.44C354.4 86.4 323.6 96.28 301.9 117.1L255.1 163.9z\"/><\/svg><svg aria-hidden=\"true\" role=\"img\" viewBox=\"0 0 512 512\" style=\"height:1em;width:1em;vertical-align:-0.125em;margin-left:auto;margin-right:auto;font-size:inherit;fill:currentColor;overflow:visible;position:relative;\"><path d=\"M244 84L255.1 96L267.1 84.02C300.6 51.37 347 36.51 392.6 44.1C461.5 55.58 512 115.2 512 185.1V190.9C512 232.4 494.8 272.1 464.4 300.4L283.7 469.1C276.2 476.1 266.3 480 256 480C245.7 480 235.8 476.1 228.3 469.1L47.59 300.4C17.23 272.1 0 232.4 0 190.9V185.1C0 115.2 50.52 55.58 119.4 44.1C164.1 36.51 211.4 51.37 244 84C243.1 84 244 84.01 244 84L244 84zM255.1 163.9L210.1 117.1C188.4 96.28 157.6 86.4 127.3 91.44C81.55 99.07 48 138.7 48 185.1V190.9C48 219.1 59.71 246.1 80.34 265.3L256 429.3L431.7 265.3C452.3 246.1 464 219.1 464 190.9V185.1C464 138.7 430.4 99.07 384.7 91.44C354.4 86.4 323.6 96.28 301.9 117.1L255.1 163.9z\"/><\/svg><svg aria-hidden=\"true\" role=\"img\" viewBox=\"0 0 512 512\" style=\"height:1em;width:1em;vertical-align:-0.125em;margin-left:auto;margin-right:auto;font-size:inherit;fill:currentColor;overflow:visible;position:relative;\"><path d=\"M244 84L255.1 96L267.1 84.02C300.6 51.37 347 36.51 392.6 44.1C461.5 55.58 512 115.2 512 185.1V190.9C512 232.4 494.8 272.1 464.4 300.4L283.7 469.1C276.2 476.1 266.3 480 256 480C245.7 480 235.8 476.1 228.3 469.1L47.59 300.4C17.23 272.1 0 232.4 0 190.9V185.1C0 115.2 50.52 55.58 119.4 44.1C164.1 36.51 211.4 51.37 244 84C243.1 84 244 84.01 244 84L244 84zM255.1 163.9L210.1 117.1C188.4 96.28 157.6 86.4 127.3 91.44C81.55 99.07 48 138.7 48 185.1V190.9C48 219.1 59.71 246.1 80.34 265.3L256 429.3L431.7 265.3C452.3 246.1 464 219.1 464 190.9V185.1C464 138.7 430.4 99.07 384.7 91.44C354.4 86.4 323.6 96.28 301.9 117.1L255.1 163.9z\"/><\/svg>","<svg aria-hidden=\"true\" role=\"img\" viewBox=\"0 0 512 512\" style=\"height:1em;width:1em;vertical-align:-0.125em;margin-left:auto;margin-right:auto;font-size:inherit;fill:currentColor;overflow:visible;position:relative;\"><path d=\"M244 84L255.1 96L267.1 84.02C300.6 51.37 347 36.51 392.6 44.1C461.5 55.58 512 115.2 512 185.1V190.9C512 232.4 494.8 272.1 464.4 300.4L283.7 469.1C276.2 476.1 266.3 480 256 480C245.7 480 235.8 476.1 228.3 469.1L47.59 300.4C17.23 272.1 0 232.4 0 190.9V185.1C0 115.2 50.52 55.58 119.4 44.1C164.1 36.51 211.4 51.37 244 84C243.1 84 244 84.01 244 84L244 84zM255.1 163.9L210.1 117.1C188.4 96.28 157.6 86.4 127.3 91.44C81.55 99.07 48 138.7 48 185.1V190.9C48 219.1 59.71 246.1 80.34 265.3L256 429.3L431.7 265.3C452.3 246.1 464 219.1 464 190.9V185.1C464 138.7 430.4 99.07 384.7 91.44C354.4 86.4 323.6 96.28 301.9 117.1L255.1 163.9z\"/><\/svg><svg aria-hidden=\"true\" role=\"img\" viewBox=\"0 0 512 512\" style=\"height:1em;width:1em;vertical-align:-0.125em;margin-left:auto;margin-right:auto;font-size:inherit;fill:currentColor;overflow:visible;position:relative;\"><path d=\"M244 84L255.1 96L267.1 84.02C300.6 51.37 347 36.51 392.6 44.1C461.5 55.58 512 115.2 512 185.1V190.9C512 232.4 494.8 272.1 464.4 300.4L283.7 469.1C276.2 476.1 266.3 480 256 480C245.7 480 235.8 476.1 228.3 469.1L47.59 300.4C17.23 272.1 0 232.4 0 190.9V185.1C0 115.2 50.52 55.58 119.4 44.1C164.1 36.51 211.4 51.37 244 84C243.1 84 244 84.01 244 84L244 84zM255.1 163.9L210.1 117.1C188.4 96.28 157.6 86.4 127.3 91.44C81.55 99.07 48 138.7 48 185.1V190.9C48 219.1 59.71 246.1 80.34 265.3L256 429.3L431.7 265.3C452.3 246.1 464 219.1 464 190.9V185.1C464 138.7 430.4 99.07 384.7 91.44C354.4 86.4 323.6 96.28 301.9 117.1L255.1 163.9z\"/><\/svg>","<svg aria-hidden=\"true\" role=\"img\" viewBox=\"0 0 512 512\" style=\"height:1em;width:1em;vertical-align:-0.125em;margin-left:auto;margin-right:auto;font-size:inherit;fill:currentColor;overflow:visible;position:relative;\"><path d=\"M244 84L255.1 96L267.1 84.02C300.6 51.37 347 36.51 392.6 44.1C461.5 55.58 512 115.2 512 185.1V190.9C512 232.4 494.8 272.1 464.4 300.4L283.7 469.1C276.2 476.1 266.3 480 256 480C245.7 480 235.8 476.1 228.3 469.1L47.59 300.4C17.23 272.1 0 232.4 0 190.9V185.1C0 115.2 50.52 55.58 119.4 44.1C164.1 36.51 211.4 51.37 244 84C243.1 84 244 84.01 244 84L244 84zM255.1 163.9L210.1 117.1C188.4 96.28 157.6 86.4 127.3 91.44C81.55 99.07 48 138.7 48 185.1V190.9C48 219.1 59.71 246.1 80.34 265.3L256 429.3L431.7 265.3C452.3 246.1 464 219.1 464 190.9V185.1C464 138.7 430.4 99.07 384.7 91.44C354.4 86.4 323.6 96.28 301.9 117.1L255.1 163.9z\"/><\/svg><svg aria-hidden=\"true\" role=\"img\" viewBox=\"0 0 512 512\" style=\"height:1em;width:1em;vertical-align:-0.125em;margin-left:auto;margin-right:auto;font-size:inherit;fill:currentColor;overflow:visible;position:relative;\"><path d=\"M244 84L255.1 96L267.1 84.02C300.6 51.37 347 36.51 392.6 44.1C461.5 55.58 512 115.2 512 185.1V190.9C512 232.4 494.8 272.1 464.4 300.4L283.7 469.1C276.2 476.1 266.3 480 256 480C245.7 480 235.8 476.1 228.3 469.1L47.59 300.4C17.23 272.1 0 232.4 0 190.9V185.1C0 115.2 50.52 55.58 119.4 44.1C164.1 36.51 211.4 51.37 244 84C243.1 84 244 84.01 244 84L244 84zM255.1 163.9L210.1 117.1C188.4 96.28 157.6 86.4 127.3 91.44C81.55 99.07 48 138.7 48 185.1V190.9C48 219.1 59.71 246.1 80.34 265.3L256 429.3L431.7 265.3C452.3 246.1 464 219.1 464 190.9V185.1C464 138.7 430.4 99.07 384.7 91.44C354.4 86.4 323.6 96.28 301.9 117.1L255.1 163.9z\"/><\/svg><svg aria-hidden=\"true\" role=\"img\" viewBox=\"0 0 512 512\" style=\"height:1em;width:1em;vertical-align:-0.125em;margin-left:auto;margin-right:auto;font-size:inherit;fill:currentColor;overflow:visible;position:relative;\"><path d=\"M244 84L255.1 96L267.1 84.02C300.6 51.37 347 36.51 392.6 44.1C461.5 55.58 512 115.2 512 185.1V190.9C512 232.4 494.8 272.1 464.4 300.4L283.7 469.1C276.2 476.1 266.3 480 256 480C245.7 480 235.8 476.1 228.3 469.1L47.59 300.4C17.23 272.1 0 232.4 0 190.9V185.1C0 115.2 50.52 55.58 119.4 44.1C164.1 36.51 211.4 51.37 244 84C243.1 84 244 84.01 244 84L244 84zM255.1 163.9L210.1 117.1C188.4 96.28 157.6 86.4 127.3 91.44C81.55 99.07 48 138.7 48 185.1V190.9C48 219.1 59.71 246.1 80.34 265.3L256 429.3L431.7 265.3C452.3 246.1 464 219.1 464 190.9V185.1C464 138.7 430.4 99.07 384.7 91.44C354.4 86.4 323.6 96.28 301.9 117.1L255.1 163.9z\"/><\/svg>","<svg aria-hidden=\"true\" role=\"img\" viewBox=\"0 0 512 512\" style=\"height:1em;width:1em;vertical-align:-0.125em;margin-left:auto;margin-right:auto;font-size:inherit;fill:currentColor;overflow:visible;position:relative;\"><path d=\"M244 84L255.1 96L267.1 84.02C300.6 51.37 347 36.51 392.6 44.1C461.5 55.58 512 115.2 512 185.1V190.9C512 232.4 494.8 272.1 464.4 300.4L283.7 469.1C276.2 476.1 266.3 480 256 480C245.7 480 235.8 476.1 228.3 469.1L47.59 300.4C17.23 272.1 0 232.4 0 190.9V185.1C0 115.2 50.52 55.58 119.4 44.1C164.1 36.51 211.4 51.37 244 84C243.1 84 244 84.01 244 84L244 84zM255.1 163.9L210.1 117.1C188.4 96.28 157.6 86.4 127.3 91.44C81.55 99.07 48 138.7 48 185.1V190.9C48 219.1 59.71 246.1 80.34 265.3L256 429.3L431.7 265.3C452.3 246.1 464 219.1 464 190.9V185.1C464 138.7 430.4 99.07 384.7 91.44C354.4 86.4 323.6 96.28 301.9 117.1L255.1 163.9z\"/><\/svg><svg aria-hidden=\"true\" role=\"img\" viewBox=\"0 0 512 512\" style=\"height:1em;width:1em;vertical-align:-0.125em;margin-left:auto;margin-right:auto;font-size:inherit;fill:currentColor;overflow:visible;position:relative;\"><path d=\"M244 84L255.1 96L267.1 84.02C300.6 51.37 347 36.51 392.6 44.1C461.5 55.58 512 115.2 512 185.1V190.9C512 232.4 494.8 272.1 464.4 300.4L283.7 469.1C276.2 476.1 266.3 480 256 480C245.7 480 235.8 476.1 228.3 469.1L47.59 300.4C17.23 272.1 0 232.4 0 190.9V185.1C0 115.2 50.52 55.58 119.4 44.1C164.1 36.51 211.4 51.37 244 84C243.1 84 244 84.01 244 84L244 84zM255.1 163.9L210.1 117.1C188.4 96.28 157.6 86.4 127.3 91.44C81.55 99.07 48 138.7 48 185.1V190.9C48 219.1 59.71 246.1 80.34 265.3L256 429.3L431.7 265.3C452.3 246.1 464 219.1 464 190.9V185.1C464 138.7 430.4 99.07 384.7 91.44C354.4 86.4 323.6 96.28 301.9 117.1L255.1 163.9z\"/><\/svg>","<svg aria-hidden=\"true\" role=\"img\" viewBox=\"0 0 512 512\" style=\"height:1em;width:1em;vertical-align:-0.125em;margin-left:auto;margin-right:auto;font-size:inherit;fill:currentColor;overflow:visible;position:relative;\"><path d=\"M244 84L255.1 96L267.1 84.02C300.6 51.37 347 36.51 392.6 44.1C461.5 55.58 512 115.2 512 185.1V190.9C512 232.4 494.8 272.1 464.4 300.4L283.7 469.1C276.2 476.1 266.3 480 256 480C245.7 480 235.8 476.1 228.3 469.1L47.59 300.4C17.23 272.1 0 232.4 0 190.9V185.1C0 115.2 50.52 55.58 119.4 44.1C164.1 36.51 211.4 51.37 244 84C243.1 84 244 84.01 244 84L244 84zM255.1 163.9L210.1 117.1C188.4 96.28 157.6 86.4 127.3 91.44C81.55 99.07 48 138.7 48 185.1V190.9C48 219.1 59.71 246.1 80.34 265.3L256 429.3L431.7 265.3C452.3 246.1 464 219.1 464 190.9V185.1C464 138.7 430.4 99.07 384.7 91.44C354.4 86.4 323.6 96.28 301.9 117.1L255.1 163.9z\"/><\/svg>","<svg aria-hidden=\"true\" role=\"img\" viewBox=\"0 0 512 512\" style=\"height:1em;width:1em;vertical-align:-0.125em;margin-left:auto;margin-right:auto;font-size:inherit;fill:currentColor;overflow:visible;position:relative;\"><path d=\"M244 84L255.1 96L267.1 84.02C300.6 51.37 347 36.51 392.6 44.1C461.5 55.58 512 115.2 512 185.1V190.9C512 232.4 494.8 272.1 464.4 300.4L283.7 469.1C276.2 476.1 266.3 480 256 480C245.7 480 235.8 476.1 228.3 469.1L47.59 300.4C17.23 272.1 0 232.4 0 190.9V185.1C0 115.2 50.52 55.58 119.4 44.1C164.1 36.51 211.4 51.37 244 84C243.1 84 244 84.01 244 84L244 84zM255.1 163.9L210.1 117.1C188.4 96.28 157.6 86.4 127.3 91.44C81.55 99.07 48 138.7 48 185.1V190.9C48 219.1 59.71 246.1 80.34 265.3L256 429.3L431.7 265.3C452.3 246.1 464 219.1 464 190.9V185.1C464 138.7 430.4 99.07 384.7 91.44C354.4 86.4 323.6 96.28 301.9 117.1L255.1 163.9z\"/><\/svg><svg aria-hidden=\"true\" role=\"img\" viewBox=\"0 0 512 512\" style=\"height:1em;width:1em;vertical-align:-0.125em;margin-left:auto;margin-right:auto;font-size:inherit;fill:currentColor;overflow:visible;position:relative;\"><path d=\"M244 84L255.1 96L267.1 84.02C300.6 51.37 347 36.51 392.6 44.1C461.5 55.58 512 115.2 512 185.1V190.9C512 232.4 494.8 272.1 464.4 300.4L283.7 469.1C276.2 476.1 266.3 480 256 480C245.7 480 235.8 476.1 228.3 469.1L47.59 300.4C17.23 272.1 0 232.4 0 190.9V185.1C0 115.2 50.52 55.58 119.4 44.1C164.1 36.51 211.4 51.37 244 84C243.1 84 244 84.01 244 84L244 84zM255.1 163.9L210.1 117.1C188.4 96.28 157.6 86.4 127.3 91.44C81.55 99.07 48 138.7 48 185.1V190.9C48 219.1 59.71 246.1 80.34 265.3L256 429.3L431.7 265.3C452.3 246.1 464 219.1 464 190.9V185.1C464 138.7 430.4 99.07 384.7 91.44C354.4 86.4 323.6 96.28 301.9 117.1L255.1 163.9z\"/><\/svg><svg aria-hidden=\"true\" role=\"img\" viewBox=\"0 0 512 512\" style=\"height:1em;width:1em;vertical-align:-0.125em;margin-left:auto;margin-right:auto;font-size:inherit;fill:currentColor;overflow:visible;position:relative;\"><path d=\"M244 84L255.1 96L267.1 84.02C300.6 51.37 347 36.51 392.6 44.1C461.5 55.58 512 115.2 512 185.1V190.9C512 232.4 494.8 272.1 464.4 300.4L283.7 469.1C276.2 476.1 266.3 480 256 480C245.7 480 235.8 476.1 228.3 469.1L47.59 300.4C17.23 272.1 0 232.4 0 190.9V185.1C0 115.2 50.52 55.58 119.4 44.1C164.1 36.51 211.4 51.37 244 84C243.1 84 244 84.01 244 84L244 84zM255.1 163.9L210.1 117.1C188.4 96.28 157.6 86.4 127.3 91.44C81.55 99.07 48 138.7 48 185.1V190.9C48 219.1 59.71 246.1 80.34 265.3L256 429.3L431.7 265.3C452.3 246.1 464 219.1 464 190.9V185.1C464 138.7 430.4 99.07 384.7 91.44C354.4 86.4 323.6 96.28 301.9 117.1L255.1 163.9z\"/><\/svg><svg aria-hidden=\"true\" role=\"img\" viewBox=\"0 0 512 512\" style=\"height:1em;width:1em;vertical-align:-0.125em;margin-left:auto;margin-right:auto;font-size:inherit;fill:currentColor;overflow:visible;position:relative;\"><path d=\"M244 84L255.1 96L267.1 84.02C300.6 51.37 347 36.51 392.6 44.1C461.5 55.58 512 115.2 512 185.1V190.9C512 232.4 494.8 272.1 464.4 300.4L283.7 469.1C276.2 476.1 266.3 480 256 480C245.7 480 235.8 476.1 228.3 469.1L47.59 300.4C17.23 272.1 0 232.4 0 190.9V185.1C0 115.2 50.52 55.58 119.4 44.1C164.1 36.51 211.4 51.37 244 84C243.1 84 244 84.01 244 84L244 84zM255.1 163.9L210.1 117.1C188.4 96.28 157.6 86.4 127.3 91.44C81.55 99.07 48 138.7 48 185.1V190.9C48 219.1 59.71 246.1 80.34 265.3L256 429.3L431.7 265.3C452.3 246.1 464 219.1 464 190.9V185.1C464 138.7 430.4 99.07 384.7 91.44C354.4 86.4 323.6 96.28 301.9 117.1L255.1 163.9z\"/><\/svg>","<svg aria-hidden=\"true\" role=\"img\" viewBox=\"0 0 512 512\" style=\"height:1em;width:1em;vertical-align:-0.125em;margin-left:auto;margin-right:auto;font-size:inherit;fill:currentColor;overflow:visible;position:relative;\"><path d=\"M244 84L255.1 96L267.1 84.02C300.6 51.37 347 36.51 392.6 44.1C461.5 55.58 512 115.2 512 185.1V190.9C512 232.4 494.8 272.1 464.4 300.4L283.7 469.1C276.2 476.1 266.3 480 256 480C245.7 480 235.8 476.1 228.3 469.1L47.59 300.4C17.23 272.1 0 232.4 0 190.9V185.1C0 115.2 50.52 55.58 119.4 44.1C164.1 36.51 211.4 51.37 244 84C243.1 84 244 84.01 244 84L244 84zM255.1 163.9L210.1 117.1C188.4 96.28 157.6 86.4 127.3 91.44C81.55 99.07 48 138.7 48 185.1V190.9C48 219.1 59.71 246.1 80.34 265.3L256 429.3L431.7 265.3C452.3 246.1 464 219.1 464 190.9V185.1C464 138.7 430.4 99.07 384.7 91.44C354.4 86.4 323.6 96.28 301.9 117.1L255.1 163.9z\"/><\/svg><svg aria-hidden=\"true\" role=\"img\" viewBox=\"0 0 512 512\" style=\"height:1em;width:1em;vertical-align:-0.125em;margin-left:auto;margin-right:auto;font-size:inherit;fill:currentColor;overflow:visible;position:relative;\"><path d=\"M244 84L255.1 96L267.1 84.02C300.6 51.37 347 36.51 392.6 44.1C461.5 55.58 512 115.2 512 185.1V190.9C512 232.4 494.8 272.1 464.4 300.4L283.7 469.1C276.2 476.1 266.3 480 256 480C245.7 480 235.8 476.1 228.3 469.1L47.59 300.4C17.23 272.1 0 232.4 0 190.9V185.1C0 115.2 50.52 55.58 119.4 44.1C164.1 36.51 211.4 51.37 244 84C243.1 84 244 84.01 244 84L244 84zM255.1 163.9L210.1 117.1C188.4 96.28 157.6 86.4 127.3 91.44C81.55 99.07 48 138.7 48 185.1V190.9C48 219.1 59.71 246.1 80.34 265.3L256 429.3L431.7 265.3C452.3 246.1 464 219.1 464 190.9V185.1C464 138.7 430.4 99.07 384.7 91.44C354.4 86.4 323.6 96.28 301.9 117.1L255.1 163.9z\"/><\/svg>","<svg aria-hidden=\"true\" role=\"img\" viewBox=\"0 0 512 512\" style=\"height:1em;width:1em;vertical-align:-0.125em;margin-left:auto;margin-right:auto;font-size:inherit;fill:currentColor;overflow:visible;position:relative;\"><path d=\"M244 84L255.1 96L267.1 84.02C300.6 51.37 347 36.51 392.6 44.1C461.5 55.58 512 115.2 512 185.1V190.9C512 232.4 494.8 272.1 464.4 300.4L283.7 469.1C276.2 476.1 266.3 480 256 480C245.7 480 235.8 476.1 228.3 469.1L47.59 300.4C17.23 272.1 0 232.4 0 190.9V185.1C0 115.2 50.52 55.58 119.4 44.1C164.1 36.51 211.4 51.37 244 84C243.1 84 244 84.01 244 84L244 84zM255.1 163.9L210.1 117.1C188.4 96.28 157.6 86.4 127.3 91.44C81.55 99.07 48 138.7 48 185.1V190.9C48 219.1 59.71 246.1 80.34 265.3L256 429.3L431.7 265.3C452.3 246.1 464 219.1 464 190.9V185.1C464 138.7 430.4 99.07 384.7 91.44C354.4 86.4 323.6 96.28 301.9 117.1L255.1 163.9z\"/><\/svg><svg aria-hidden=\"true\" role=\"img\" viewBox=\"0 0 512 512\" style=\"height:1em;width:1em;vertical-align:-0.125em;margin-left:auto;margin-right:auto;font-size:inherit;fill:currentColor;overflow:visible;position:relative;\"><path d=\"M244 84L255.1 96L267.1 84.02C300.6 51.37 347 36.51 392.6 44.1C461.5 55.58 512 115.2 512 185.1V190.9C512 232.4 494.8 272.1 464.4 300.4L283.7 469.1C276.2 476.1 266.3 480 256 480C245.7 480 235.8 476.1 228.3 469.1L47.59 300.4C17.23 272.1 0 232.4 0 190.9V185.1C0 115.2 50.52 55.58 119.4 44.1C164.1 36.51 211.4 51.37 244 84C243.1 84 244 84.01 244 84L244 84zM255.1 163.9L210.1 117.1C188.4 96.28 157.6 86.4 127.3 91.44C81.55 99.07 48 138.7 48 185.1V190.9C48 219.1 59.71 246.1 80.34 265.3L256 429.3L431.7 265.3C452.3 246.1 464 219.1 464 190.9V185.1C464 138.7 430.4 99.07 384.7 91.44C354.4 86.4 323.6 96.28 301.9 117.1L255.1 163.9z\"/><\/svg>","<svg aria-hidden=\"true\" role=\"img\" viewBox=\"0 0 512 512\" style=\"height:1em;width:1em;vertical-align:-0.125em;margin-left:auto;margin-right:auto;font-size:inherit;fill:currentColor;overflow:visible;position:relative;\"><path d=\"M244 84L255.1 96L267.1 84.02C300.6 51.37 347 36.51 392.6 44.1C461.5 55.58 512 115.2 512 185.1V190.9C512 232.4 494.8 272.1 464.4 300.4L283.7 469.1C276.2 476.1 266.3 480 256 480C245.7 480 235.8 476.1 228.3 469.1L47.59 300.4C17.23 272.1 0 232.4 0 190.9V185.1C0 115.2 50.52 55.58 119.4 44.1C164.1 36.51 211.4 51.37 244 84C243.1 84 244 84.01 244 84L244 84zM255.1 163.9L210.1 117.1C188.4 96.28 157.6 86.4 127.3 91.44C81.55 99.07 48 138.7 48 185.1V190.9C48 219.1 59.71 246.1 80.34 265.3L256 429.3L431.7 265.3C452.3 246.1 464 219.1 464 190.9V185.1C464 138.7 430.4 99.07 384.7 91.44C354.4 86.4 323.6 96.28 301.9 117.1L255.1 163.9z\"/><\/svg><svg aria-hidden=\"true\" role=\"img\" viewBox=\"0 0 512 512\" style=\"height:1em;width:1em;vertical-align:-0.125em;margin-left:auto;margin-right:auto;font-size:inherit;fill:currentColor;overflow:visible;position:relative;\"><path d=\"M244 84L255.1 96L267.1 84.02C300.6 51.37 347 36.51 392.6 44.1C461.5 55.58 512 115.2 512 185.1V190.9C512 232.4 494.8 272.1 464.4 300.4L283.7 469.1C276.2 476.1 266.3 480 256 480C245.7 480 235.8 476.1 228.3 469.1L47.59 300.4C17.23 272.1 0 232.4 0 190.9V185.1C0 115.2 50.52 55.58 119.4 44.1C164.1 36.51 211.4 51.37 244 84C243.1 84 244 84.01 244 84L244 84zM255.1 163.9L210.1 117.1C188.4 96.28 157.6 86.4 127.3 91.44C81.55 99.07 48 138.7 48 185.1V190.9C48 219.1 59.71 246.1 80.34 265.3L256 429.3L431.7 265.3C452.3 246.1 464 219.1 464 190.9V185.1C464 138.7 430.4 99.07 384.7 91.44C354.4 86.4 323.6 96.28 301.9 117.1L255.1 163.9z\"/><\/svg><svg aria-hidden=\"true\" role=\"img\" viewBox=\"0 0 512 512\" style=\"height:1em;width:1em;vertical-align:-0.125em;margin-left:auto;margin-right:auto;font-size:inherit;fill:currentColor;overflow:visible;position:relative;\"><path d=\"M244 84L255.1 96L267.1 84.02C300.6 51.37 347 36.51 392.6 44.1C461.5 55.58 512 115.2 512 185.1V190.9C512 232.4 494.8 272.1 464.4 300.4L283.7 469.1C276.2 476.1 266.3 480 256 480C245.7 480 235.8 476.1 228.3 469.1L47.59 300.4C17.23 272.1 0 232.4 0 190.9V185.1C0 115.2 50.52 55.58 119.4 44.1C164.1 36.51 211.4 51.37 244 84C243.1 84 244 84.01 244 84L244 84zM255.1 163.9L210.1 117.1C188.4 96.28 157.6 86.4 127.3 91.44C81.55 99.07 48 138.7 48 185.1V190.9C48 219.1 59.71 246.1 80.34 265.3L256 429.3L431.7 265.3C452.3 246.1 464 219.1 464 190.9V185.1C464 138.7 430.4 99.07 384.7 91.44C354.4 86.4 323.6 96.28 301.9 117.1L255.1 163.9z\"/><\/svg><svg aria-hidden=\"true\" role=\"img\" viewBox=\"0 0 512 512\" style=\"height:1em;width:1em;vertical-align:-0.125em;margin-left:auto;margin-right:auto;font-size:inherit;fill:currentColor;overflow:visible;position:relative;\"><path d=\"M244 84L255.1 96L267.1 84.02C300.6 51.37 347 36.51 392.6 44.1C461.5 55.58 512 115.2 512 185.1V190.9C512 232.4 494.8 272.1 464.4 300.4L283.7 469.1C276.2 476.1 266.3 480 256 480C245.7 480 235.8 476.1 228.3 469.1L47.59 300.4C17.23 272.1 0 232.4 0 190.9V185.1C0 115.2 50.52 55.58 119.4 44.1C164.1 36.51 211.4 51.37 244 84C243.1 84 244 84.01 244 84L244 84zM255.1 163.9L210.1 117.1C188.4 96.28 157.6 86.4 127.3 91.44C81.55 99.07 48 138.7 48 185.1V190.9C48 219.1 59.71 246.1 80.34 265.3L256 429.3L431.7 265.3C452.3 246.1 464 219.1 464 190.9V185.1C464 138.7 430.4 99.07 384.7 91.44C354.4 86.4 323.6 96.28 301.9 117.1L255.1 163.9z\"/><\/svg><svg aria-hidden=\"true\" role=\"img\" viewBox=\"0 0 512 512\" style=\"height:1em;width:1em;vertical-align:-0.125em;margin-left:auto;margin-right:auto;font-size:inherit;fill:currentColor;overflow:visible;position:relative;\"><path d=\"M244 84L255.1 96L267.1 84.02C300.6 51.37 347 36.51 392.6 44.1C461.5 55.58 512 115.2 512 185.1V190.9C512 232.4 494.8 272.1 464.4 300.4L283.7 469.1C276.2 476.1 266.3 480 256 480C245.7 480 235.8 476.1 228.3 469.1L47.59 300.4C17.23 272.1 0 232.4 0 190.9V185.1C0 115.2 50.52 55.58 119.4 44.1C164.1 36.51 211.4 51.37 244 84C243.1 84 244 84.01 244 84L244 84zM255.1 163.9L210.1 117.1C188.4 96.28 157.6 86.4 127.3 91.44C81.55 99.07 48 138.7 48 185.1V190.9C48 219.1 59.71 246.1 80.34 265.3L256 429.3L431.7 265.3C452.3 246.1 464 219.1 464 190.9V185.1C464 138.7 430.4 99.07 384.7 91.44C354.4 86.4 323.6 96.28 301.9 117.1L255.1 163.9z\"/><\/svg>","<svg aria-hidden=\"true\" role=\"img\" viewBox=\"0 0 512 512\" style=\"height:1em;width:1em;vertical-align:-0.125em;margin-left:auto;margin-right:auto;font-size:inherit;fill:currentColor;overflow:visible;position:relative;\"><path d=\"M244 84L255.1 96L267.1 84.02C300.6 51.37 347 36.51 392.6 44.1C461.5 55.58 512 115.2 512 185.1V190.9C512 232.4 494.8 272.1 464.4 300.4L283.7 469.1C276.2 476.1 266.3 480 256 480C245.7 480 235.8 476.1 228.3 469.1L47.59 300.4C17.23 272.1 0 232.4 0 190.9V185.1C0 115.2 50.52 55.58 119.4 44.1C164.1 36.51 211.4 51.37 244 84C243.1 84 244 84.01 244 84L244 84zM255.1 163.9L210.1 117.1C188.4 96.28 157.6 86.4 127.3 91.44C81.55 99.07 48 138.7 48 185.1V190.9C48 219.1 59.71 246.1 80.34 265.3L256 429.3L431.7 265.3C452.3 246.1 464 219.1 464 190.9V185.1C464 138.7 430.4 99.07 384.7 91.44C354.4 86.4 323.6 96.28 301.9 117.1L255.1 163.9z\"/><\/svg><svg aria-hidden=\"true\" role=\"img\" viewBox=\"0 0 512 512\" style=\"height:1em;width:1em;vertical-align:-0.125em;margin-left:auto;margin-right:auto;font-size:inherit;fill:currentColor;overflow:visible;position:relative;\"><path d=\"M244 84L255.1 96L267.1 84.02C300.6 51.37 347 36.51 392.6 44.1C461.5 55.58 512 115.2 512 185.1V190.9C512 232.4 494.8 272.1 464.4 300.4L283.7 469.1C276.2 476.1 266.3 480 256 480C245.7 480 235.8 476.1 228.3 469.1L47.59 300.4C17.23 272.1 0 232.4 0 190.9V185.1C0 115.2 50.52 55.58 119.4 44.1C164.1 36.51 211.4 51.37 244 84C243.1 84 244 84.01 244 84L244 84zM255.1 163.9L210.1 117.1C188.4 96.28 157.6 86.4 127.3 91.44C81.55 99.07 48 138.7 48 185.1V190.9C48 219.1 59.71 246.1 80.34 265.3L256 429.3L431.7 265.3C452.3 246.1 464 219.1 464 190.9V185.1C464 138.7 430.4 99.07 384.7 91.44C354.4 86.4 323.6 96.28 301.9 117.1L255.1 163.9z\"/><\/svg><svg aria-hidden=\"true\" role=\"img\" viewBox=\"0 0 512 512\" style=\"height:1em;width:1em;vertical-align:-0.125em;margin-left:auto;margin-right:auto;font-size:inherit;fill:currentColor;overflow:visible;position:relative;\"><path d=\"M244 84L255.1 96L267.1 84.02C300.6 51.37 347 36.51 392.6 44.1C461.5 55.58 512 115.2 512 185.1V190.9C512 232.4 494.8 272.1 464.4 300.4L283.7 469.1C276.2 476.1 266.3 480 256 480C245.7 480 235.8 476.1 228.3 469.1L47.59 300.4C17.23 272.1 0 232.4 0 190.9V185.1C0 115.2 50.52 55.58 119.4 44.1C164.1 36.51 211.4 51.37 244 84C243.1 84 244 84.01 244 84L244 84zM255.1 163.9L210.1 117.1C188.4 96.28 157.6 86.4 127.3 91.44C81.55 99.07 48 138.7 48 185.1V190.9C48 219.1 59.71 246.1 80.34 265.3L256 429.3L431.7 265.3C452.3 246.1 464 219.1 464 190.9V185.1C464 138.7 430.4 99.07 384.7 91.44C354.4 86.4 323.6 96.28 301.9 117.1L255.1 163.9z\"/><\/svg><svg aria-hidden=\"true\" role=\"img\" viewBox=\"0 0 512 512\" style=\"height:1em;width:1em;vertical-align:-0.125em;margin-left:auto;margin-right:auto;font-size:inherit;fill:currentColor;overflow:visible;position:relative;\"><path d=\"M244 84L255.1 96L267.1 84.02C300.6 51.37 347 36.51 392.6 44.1C461.5 55.58 512 115.2 512 185.1V190.9C512 232.4 494.8 272.1 464.4 300.4L283.7 469.1C276.2 476.1 266.3 480 256 480C245.7 480 235.8 476.1 228.3 469.1L47.59 300.4C17.23 272.1 0 232.4 0 190.9V185.1C0 115.2 50.52 55.58 119.4 44.1C164.1 36.51 211.4 51.37 244 84C243.1 84 244 84.01 244 84L244 84zM255.1 163.9L210.1 117.1C188.4 96.28 157.6 86.4 127.3 91.44C81.55 99.07 48 138.7 48 185.1V190.9C48 219.1 59.71 246.1 80.34 265.3L256 429.3L431.7 265.3C452.3 246.1 464 219.1 464 190.9V185.1C464 138.7 430.4 99.07 384.7 91.44C354.4 86.4 323.6 96.28 301.9 117.1L255.1 163.9z\"/><\/svg><svg aria-hidden=\"true\" role=\"img\" viewBox=\"0 0 512 512\" style=\"height:1em;width:1em;vertical-align:-0.125em;margin-left:auto;margin-right:auto;font-size:inherit;fill:currentColor;overflow:visible;position:relative;\"><path d=\"M244 84L255.1 96L267.1 84.02C300.6 51.37 347 36.51 392.6 44.1C461.5 55.58 512 115.2 512 185.1V190.9C512 232.4 494.8 272.1 464.4 300.4L283.7 469.1C276.2 476.1 266.3 480 256 480C245.7 480 235.8 476.1 228.3 469.1L47.59 300.4C17.23 272.1 0 232.4 0 190.9V185.1C0 115.2 50.52 55.58 119.4 44.1C164.1 36.51 211.4 51.37 244 84C243.1 84 244 84.01 244 84L244 84zM255.1 163.9L210.1 117.1C188.4 96.28 157.6 86.4 127.3 91.44C81.55 99.07 48 138.7 48 185.1V190.9C48 219.1 59.71 246.1 80.34 265.3L256 429.3L431.7 265.3C452.3 246.1 464 219.1 464 190.9V185.1C464 138.7 430.4 99.07 384.7 91.44C354.4 86.4 323.6 96.28 301.9 117.1L255.1 163.9z\"/><\/svg>","<svg aria-hidden=\"true\" role=\"img\" viewBox=\"0 0 512 512\" style=\"height:1em;width:1em;vertical-align:-0.125em;margin-left:auto;margin-right:auto;font-size:inherit;fill:currentColor;overflow:visible;position:relative;\"><path d=\"M244 84L255.1 96L267.1 84.02C300.6 51.37 347 36.51 392.6 44.1C461.5 55.58 512 115.2 512 185.1V190.9C512 232.4 494.8 272.1 464.4 300.4L283.7 469.1C276.2 476.1 266.3 480 256 480C245.7 480 235.8 476.1 228.3 469.1L47.59 300.4C17.23 272.1 0 232.4 0 190.9V185.1C0 115.2 50.52 55.58 119.4 44.1C164.1 36.51 211.4 51.37 244 84C243.1 84 244 84.01 244 84L244 84zM255.1 163.9L210.1 117.1C188.4 96.28 157.6 86.4 127.3 91.44C81.55 99.07 48 138.7 48 185.1V190.9C48 219.1 59.71 246.1 80.34 265.3L256 429.3L431.7 265.3C452.3 246.1 464 219.1 464 190.9V185.1C464 138.7 430.4 99.07 384.7 91.44C354.4 86.4 323.6 96.28 301.9 117.1L255.1 163.9z\"/><\/svg>","<svg aria-hidden=\"true\" role=\"img\" viewBox=\"0 0 512 512\" style=\"height:1em;width:1em;vertical-align:-0.125em;margin-left:auto;margin-right:auto;font-size:inherit;fill:currentColor;overflow:visible;position:relative;\"><path d=\"M244 84L255.1 96L267.1 84.02C300.6 51.37 347 36.51 392.6 44.1C461.5 55.58 512 115.2 512 185.1V190.9C512 232.4 494.8 272.1 464.4 300.4L283.7 469.1C276.2 476.1 266.3 480 256 480C245.7 480 235.8 476.1 228.3 469.1L47.59 300.4C17.23 272.1 0 232.4 0 190.9V185.1C0 115.2 50.52 55.58 119.4 44.1C164.1 36.51 211.4 51.37 244 84C243.1 84 244 84.01 244 84L244 84zM255.1 163.9L210.1 117.1C188.4 96.28 157.6 86.4 127.3 91.44C81.55 99.07 48 138.7 48 185.1V190.9C48 219.1 59.71 246.1 80.34 265.3L256 429.3L431.7 265.3C452.3 246.1 464 219.1 464 190.9V185.1C464 138.7 430.4 99.07 384.7 91.44C354.4 86.4 323.6 96.28 301.9 117.1L255.1 163.9z\"/><\/svg><svg aria-hidden=\"true\" role=\"img\" viewBox=\"0 0 512 512\" style=\"height:1em;width:1em;vertical-align:-0.125em;margin-left:auto;margin-right:auto;font-size:inherit;fill:currentColor;overflow:visible;position:relative;\"><path d=\"M244 84L255.1 96L267.1 84.02C300.6 51.37 347 36.51 392.6 44.1C461.5 55.58 512 115.2 512 185.1V190.9C512 232.4 494.8 272.1 464.4 300.4L283.7 469.1C276.2 476.1 266.3 480 256 480C245.7 480 235.8 476.1 228.3 469.1L47.59 300.4C17.23 272.1 0 232.4 0 190.9V185.1C0 115.2 50.52 55.58 119.4 44.1C164.1 36.51 211.4 51.37 244 84C243.1 84 244 84.01 244 84L244 84zM255.1 163.9L210.1 117.1C188.4 96.28 157.6 86.4 127.3 91.44C81.55 99.07 48 138.7 48 185.1V190.9C48 219.1 59.71 246.1 80.34 265.3L256 429.3L431.7 265.3C452.3 246.1 464 219.1 464 190.9V185.1C464 138.7 430.4 99.07 384.7 91.44C354.4 86.4 323.6 96.28 301.9 117.1L255.1 163.9z\"/><\/svg>","<svg aria-hidden=\"true\" role=\"img\" viewBox=\"0 0 512 512\" style=\"height:1em;width:1em;vertical-align:-0.125em;margin-left:auto;margin-right:auto;font-size:inherit;fill:currentColor;overflow:visible;position:relative;\"><path d=\"M244 84L255.1 96L267.1 84.02C300.6 51.37 347 36.51 392.6 44.1C461.5 55.58 512 115.2 512 185.1V190.9C512 232.4 494.8 272.1 464.4 300.4L283.7 469.1C276.2 476.1 266.3 480 256 480C245.7 480 235.8 476.1 228.3 469.1L47.59 300.4C17.23 272.1 0 232.4 0 190.9V185.1C0 115.2 50.52 55.58 119.4 44.1C164.1 36.51 211.4 51.37 244 84C243.1 84 244 84.01 244 84L244 84zM255.1 163.9L210.1 117.1C188.4 96.28 157.6 86.4 127.3 91.44C81.55 99.07 48 138.7 48 185.1V190.9C48 219.1 59.71 246.1 80.34 265.3L256 429.3L431.7 265.3C452.3 246.1 464 219.1 464 190.9V185.1C464 138.7 430.4 99.07 384.7 91.44C354.4 86.4 323.6 96.28 301.9 117.1L255.1 163.9z\"/><\/svg><svg aria-hidden=\"true\" role=\"img\" viewBox=\"0 0 512 512\" style=\"height:1em;width:1em;vertical-align:-0.125em;margin-left:auto;margin-right:auto;font-size:inherit;fill:currentColor;overflow:visible;position:relative;\"><path d=\"M244 84L255.1 96L267.1 84.02C300.6 51.37 347 36.51 392.6 44.1C461.5 55.58 512 115.2 512 185.1V190.9C512 232.4 494.8 272.1 464.4 300.4L283.7 469.1C276.2 476.1 266.3 480 256 480C245.7 480 235.8 476.1 228.3 469.1L47.59 300.4C17.23 272.1 0 232.4 0 190.9V185.1C0 115.2 50.52 55.58 119.4 44.1C164.1 36.51 211.4 51.37 244 84C243.1 84 244 84.01 244 84L244 84zM255.1 163.9L210.1 117.1C188.4 96.28 157.6 86.4 127.3 91.44C81.55 99.07 48 138.7 48 185.1V190.9C48 219.1 59.71 246.1 80.34 265.3L256 429.3L431.7 265.3C452.3 246.1 464 219.1 464 190.9V185.1C464 138.7 430.4 99.07 384.7 91.44C354.4 86.4 323.6 96.28 301.9 117.1L255.1 163.9z\"/><\/svg>"]],"container":"<table class=\"display\">\n  <thead>\n    <tr>\n      <th> <\/th>\n      <th>type1<\/th>\n      <th>type2<\/th>\n      <th>value<\/th>\n      <th>value1<\/th>\n      <th>value2<\/th>\n      <th>prob1<\/th>\n      <th>prob2<\/th>\n      <th>score<\/th>\n    <\/tr>\n  <\/thead>\n<\/table>","options":{"pageLength":5,"dom":"ftip","columnDefs":[{"className":"dt-right","targets":[3,4,5,6,7]},{"orderable":false,"targets":0}],"order":[],"autoWidth":false,"orderClasses":false,"lengthMenu":[5,10,25,50,100]}},"evals":[],"jsHooks":[]}</script>

### 1.6.7.文本换行问题

DT 默认在展示文本时自动换行，可以通过单独设置列的宽度或文本对齐属性来改变换行效果。下面编造了一个由长文本组成的数据框，涵盖了三种情况：长文本，列的单元格内容比列名更长，列的列名比单元格内容更长。

``` r
textdata <- data.frame(
  "姓名" = c("蒙奇·D·路飞", "乌索普", "娜美", "托尼托尼·乔巴", "尼可·罗宾"),
  "简介" = c(
    "草帽海贼团船长，橡胶人，不导电，头脑简单，喜欢吃肉，喜欢冒险，每个伙伴都是拿命拼回来的，有点路痴",
    "狙击手，战场奇兵",
    "航海士",
    "蓝鼻子医生",
    "历史学家"
  ),
  "悬赏金额" = rep("内容比字段名长", 5),
  "角色设定&人物经历" = rep("略", 5) 
)

datatable(textdata)
```

<div id="htmlwidget-43" style="width:100%;height:auto;" class="datatables html-widget"></div>
<script type="application/json" data-for="htmlwidget-43">{"x":{"filter":"none","vertical":false,"data":[["1","2","3","4","5"],["蒙奇·D·路飞","乌索普","娜美","托尼托尼·乔巴","尼可·罗宾"],["草帽海贼团船长，橡胶人，不导电，头脑简单，喜欢吃肉，喜欢冒险，每个伙伴都是拿命拼回来的，有点路痴","狙击手，战场奇兵","航海士","蓝鼻子医生","历史学家"],["内容比字段名长","内容比字段名长","内容比字段名长","内容比字段名长","内容比字段名长"],["略","略","略","略","略"]],"container":"<table class=\"display\">\n  <thead>\n    <tr>\n      <th> <\/th>\n      <th>姓名<\/th>\n      <th>简介<\/th>\n      <th>悬赏金额<\/th>\n      <th>角色设定.人物经历<\/th>\n    <\/tr>\n  <\/thead>\n<\/table>","options":{"pageLength":5,"dom":"ftip","columnDefs":[{"orderable":false,"targets":0}],"order":[],"autoWidth":false,"orderClasses":false,"lengthMenu":[5,10,25,50,100]}},"evals":[],"jsHooks":[]}</script>

-   设置列的宽度。

``` r
datatable(textdata,
          options = list(autoWidth = TRUE,
                         columnDefs = list(
                           list(width = '100px', targets = c(1,3,4)),
                           list(width = '300px', targets =  2)
                         )))
```

<div id="htmlwidget-44" style="width:100%;height:auto;" class="datatables html-widget"></div>
<script type="application/json" data-for="htmlwidget-44">{"x":{"filter":"none","vertical":false,"data":[["1","2","3","4","5"],["蒙奇·D·路飞","乌索普","娜美","托尼托尼·乔巴","尼可·罗宾"],["草帽海贼团船长，橡胶人，不导电，头脑简单，喜欢吃肉，喜欢冒险，每个伙伴都是拿命拼回来的，有点路痴","狙击手，战场奇兵","航海士","蓝鼻子医生","历史学家"],["内容比字段名长","内容比字段名长","内容比字段名长","内容比字段名长","内容比字段名长"],["略","略","略","略","略"]],"container":"<table class=\"display\">\n  <thead>\n    <tr>\n      <th> <\/th>\n      <th>姓名<\/th>\n      <th>简介<\/th>\n      <th>悬赏金额<\/th>\n      <th>角色设定.人物经历<\/th>\n    <\/tr>\n  <\/thead>\n<\/table>","options":{"pageLength":5,"dom":"ftip","autoWidth":true,"columnDefs":[{"width":"100px","targets":[1,3,4]},{"width":"300px","targets":2},{"orderable":false,"targets":0}],"order":[],"orderClasses":false,"lengthMenu":[5,10,25,50,100]}},"evals":[],"jsHooks":[]}</script>

-   设置列的文本对齐样式。需要注意的是，若分别对同一列设置表头和表格主体的文本对齐方式，要将对表格主体的设定写在前面，否则此设定会无法生效。

``` r
datatable(textdata,
          options = list(columnDefs = list(
            list(className = 'dt-nowrap', targets = c(1, 3)),
            list(className = 'dt-body-center dt-head-nowrap', targets = 4)
          )))
```

<div id="htmlwidget-45" style="width:100%;height:auto;" class="datatables html-widget"></div>
<script type="application/json" data-for="htmlwidget-45">{"x":{"filter":"none","vertical":false,"data":[["1","2","3","4","5"],["蒙奇·D·路飞","乌索普","娜美","托尼托尼·乔巴","尼可·罗宾"],["草帽海贼团船长，橡胶人，不导电，头脑简单，喜欢吃肉，喜欢冒险，每个伙伴都是拿命拼回来的，有点路痴","狙击手，战场奇兵","航海士","蓝鼻子医生","历史学家"],["内容比字段名长","内容比字段名长","内容比字段名长","内容比字段名长","内容比字段名长"],["略","略","略","略","略"]],"container":"<table class=\"display\">\n  <thead>\n    <tr>\n      <th> <\/th>\n      <th>姓名<\/th>\n      <th>简介<\/th>\n      <th>悬赏金额<\/th>\n      <th>角色设定.人物经历<\/th>\n    <\/tr>\n  <\/thead>\n<\/table>","options":{"pageLength":5,"dom":"ftip","columnDefs":[{"className":"dt-nowrap","targets":[1,3]},{"className":"dt-body-center dt-head-nowrap","targets":4},{"orderable":false,"targets":0}],"order":[],"autoWidth":false,"orderClasses":false,"lengthMenu":[5,10,25,50,100]}},"evals":[],"jsHooks":[]}</script>

## 1.7.引入迷你图（sparkline）

### 1.7.1.折柱图

R 中的 sparkline 包是 [jQuery Sparklines](https://omnipotent.net/jquery.sparkline/#s-about) 的 R 版本，所引入的各类图形有许多参数可以自定义。由于笔者对 data.table 相对更熟一些，本小节与数据处理相关的部分均应用 data.table 来完成。这里有[一篇笔记](https://yuanfan.rbind.io/project/r-sparkline/)记录了在 DT、reactable、formattable 等表格包中引入 sparkline 的 data.table 版本和 tidyverse 版本的代码。

``` r
library(sparkline)

dt <- as.data.table(data)

spark_html <- function(...) {
  as.character(htmltools::as.tags(sparkline(..., height = 100, width=100)))}

dt.DT1 <- dt[, .(
  '面积图' = spark_html(value1, type = "line"),
  '柱状图' = spark_html(value1, type = "bar"),
  '折线图' = spark_html(
    value1,
    type = "line",
    lineColor = "red", # 折线的颜色
    fillColor = FALSE # 不展示折线下的面积
  ),
  '柱状图2' = spark_html(value1, type = "bar", barColor = "green"),
  '箱图' = spark_html(value1, type = "box")
),  keyby = .(type2)]

datatable(dt.DT1,  escape = FALSE) |> spk_add_deps()
```

<div id="htmlwidget-46" style="width:100%;height:auto;" class="datatables html-widget"></div>
<script type="application/json" data-for="htmlwidget-46">{"x":{"filter":"none","vertical":false,"data":[["1","2"],["NO","YES"],["<span id=\"htmlwidget-a210a623023e625a475d\" class=\"sparkline html-widget\"><\/span>\n<script type=\"application/json\" data-for=\"htmlwidget-a210a623023e625a475d\">{\"x\":{\"values\":[1134,1510,1224,1242,1529,1584,202,1726,1855,1834,987,798,550,1100,1777,543,1688,345,1420,1229],\"options\":{\"type\":\"line\",\"height\":100,\"width\":100},\"width\":100,\"height\":100},\"evals\":[],\"jsHooks\":[]}<\/script>","<span id=\"htmlwidget-5f1b2da53b24e360d2b0\" class=\"sparkline html-widget\"><\/span>\n<script type=\"application/json\" data-for=\"htmlwidget-5f1b2da53b24e360d2b0\">{\"x\":{\"values\":[1576,1279,581,700,624,1471,1211,1255,616,1953,1441,1542,1715,1047,1929,735,1683,1601,1333,958],\"options\":{\"type\":\"line\",\"height\":100,\"width\":100},\"width\":100,\"height\":100},\"evals\":[],\"jsHooks\":[]}<\/script>"],["<span id=\"htmlwidget-587216a772ee732c3f53\" class=\"sparkline html-widget\"><\/span>\n<script type=\"application/json\" data-for=\"htmlwidget-587216a772ee732c3f53\">{\"x\":{\"values\":[1134,1510,1224,1242,1529,1584,202,1726,1855,1834,987,798,550,1100,1777,543,1688,345,1420,1229],\"options\":{\"type\":\"bar\",\"height\":100,\"width\":100},\"width\":100,\"height\":100},\"evals\":[],\"jsHooks\":[]}<\/script>","<span id=\"htmlwidget-ae31f45872fd18730649\" class=\"sparkline html-widget\"><\/span>\n<script type=\"application/json\" data-for=\"htmlwidget-ae31f45872fd18730649\">{\"x\":{\"values\":[1576,1279,581,700,624,1471,1211,1255,616,1953,1441,1542,1715,1047,1929,735,1683,1601,1333,958],\"options\":{\"type\":\"bar\",\"height\":100,\"width\":100},\"width\":100,\"height\":100},\"evals\":[],\"jsHooks\":[]}<\/script>"],["<span id=\"htmlwidget-f94e63264c0cb1cc3345\" class=\"sparkline html-widget\"><\/span>\n<script type=\"application/json\" data-for=\"htmlwidget-f94e63264c0cb1cc3345\">{\"x\":{\"values\":[1134,1510,1224,1242,1529,1584,202,1726,1855,1834,987,798,550,1100,1777,543,1688,345,1420,1229],\"options\":{\"type\":\"line\",\"lineColor\":\"red\",\"fillColor\":false,\"height\":100,\"width\":100},\"width\":100,\"height\":100},\"evals\":[],\"jsHooks\":[]}<\/script>","<span id=\"htmlwidget-740d705a28159f71e48e\" class=\"sparkline html-widget\"><\/span>\n<script type=\"application/json\" data-for=\"htmlwidget-740d705a28159f71e48e\">{\"x\":{\"values\":[1576,1279,581,700,624,1471,1211,1255,616,1953,1441,1542,1715,1047,1929,735,1683,1601,1333,958],\"options\":{\"type\":\"line\",\"lineColor\":\"red\",\"fillColor\":false,\"height\":100,\"width\":100},\"width\":100,\"height\":100},\"evals\":[],\"jsHooks\":[]}<\/script>"],["<span id=\"htmlwidget-dc256f5f852737271537\" class=\"sparkline html-widget\"><\/span>\n<script type=\"application/json\" data-for=\"htmlwidget-dc256f5f852737271537\">{\"x\":{\"values\":[1134,1510,1224,1242,1529,1584,202,1726,1855,1834,987,798,550,1100,1777,543,1688,345,1420,1229],\"options\":{\"type\":\"bar\",\"barColor\":\"green\",\"height\":100,\"width\":100},\"width\":100,\"height\":100},\"evals\":[],\"jsHooks\":[]}<\/script>","<span id=\"htmlwidget-a0150846cfff68330fb2\" class=\"sparkline html-widget\"><\/span>\n<script type=\"application/json\" data-for=\"htmlwidget-a0150846cfff68330fb2\">{\"x\":{\"values\":[1576,1279,581,700,624,1471,1211,1255,616,1953,1441,1542,1715,1047,1929,735,1683,1601,1333,958],\"options\":{\"type\":\"bar\",\"barColor\":\"green\",\"height\":100,\"width\":100},\"width\":100,\"height\":100},\"evals\":[],\"jsHooks\":[]}<\/script>"],["<span id=\"htmlwidget-2a8422ae3bda661a0b1d\" class=\"sparkline html-widget\"><\/span>\n<script type=\"application/json\" data-for=\"htmlwidget-2a8422ae3bda661a0b1d\">{\"x\":{\"values\":[1134,1510,1224,1242,1529,1584,202,1726,1855,1834,987,798,550,1100,1777,543,1688,345,1420,1229],\"options\":{\"type\":\"box\",\"height\":100,\"width\":100},\"width\":100,\"height\":100},\"evals\":[],\"jsHooks\":[]}<\/script>","<span id=\"htmlwidget-2ef73c8153310f5e13a4\" class=\"sparkline html-widget\"><\/span>\n<script type=\"application/json\" data-for=\"htmlwidget-2ef73c8153310f5e13a4\">{\"x\":{\"values\":[1576,1279,581,700,624,1471,1211,1255,616,1953,1441,1542,1715,1047,1929,735,1683,1601,1333,958],\"options\":{\"type\":\"box\",\"height\":100,\"width\":100},\"width\":100,\"height\":100},\"evals\":[],\"jsHooks\":[]}<\/script>"]],"container":"<table class=\"display\">\n  <thead>\n    <tr>\n      <th> <\/th>\n      <th>type2<\/th>\n      <th>面积图<\/th>\n      <th>柱状图<\/th>\n      <th>折线图<\/th>\n      <th>柱状图2<\/th>\n      <th>箱图<\/th>\n    <\/tr>\n  <\/thead>\n<\/table>","options":{"pageLength":5,"dom":"ftip","columnDefs":[{"orderable":false,"targets":0}],"order":[],"autoWidth":false,"orderClasses":false,"lengthMenu":[5,10,25,50,100]}},"evals":[],"jsHooks":[]}</script>

### 1.7.2.饼图

由于 DT 包的渲染方式是一次只渲染一页数据，在有多页需要渲染迷你图时，需要在 options 中设定 `drawCallback = JS('function(s) { HTMLWidgets.staticRender(); }')`，指定每次分页时重新渲染一次。

``` r
dt.DT2 <-
  dt[, .(sparkline1 = as.character(htmltools::as.tags(
    sparkline(
      value,
      type = "pie", # 饼图
      sliceColors = c("red", "green"), # 指定饼图中各个扇形的颜色。
      offset = 90, # 指定饼图的旋转角度
      width = 50, # 指定迷你图的宽度
      height = 50 # 指定迷你图的高度
    )
  ))), keyby = .(type1)]

datatable(dt.DT2,
          escape = FALSE,
          options = list(
            dom = 'tip',
            # 每次分页重新渲染，不加这个的话只有第一页有图
            drawCallback = JS('function(s) { HTMLWidgets.staticRender(); }') 
          )) |> spk_add_deps()
```

<div id="htmlwidget-47" style="width:100%;height:auto;" class="datatables html-widget"></div>
<script type="application/json" data-for="htmlwidget-47">{"x":{"filter":"none","vertical":false,"data":[["1","2","3","4","5","6","7","8","9","10","11","12","13","14","15","16","17","18","19","20"],["A","B","C","D","E","F","G","H","I","J","K","L","M","N","O","P","Q","R","S","T"],["<span id=\"htmlwidget-e614781d09b104dae730\" class=\"sparkline html-widget\"><\/span>\n<script type=\"application/json\" data-for=\"htmlwidget-e614781d09b104dae730\">{\"x\":{\"values\":[2227,3458],\"options\":{\"type\":\"pie\",\"sliceColors\":[\"red\",\"green\"],\"offset\":90,\"height\":50,\"width\":50},\"width\":50,\"height\":50},\"evals\":[],\"jsHooks\":[]}<\/script>","<span id=\"htmlwidget-d1f2dacbee7573684b3c\" class=\"sparkline html-widget\"><\/span>\n<script type=\"application/json\" data-for=\"htmlwidget-d1f2dacbee7573684b3c\">{\"x\":{\"values\":[4870,2707],\"options\":{\"type\":\"pie\",\"sliceColors\":[\"red\",\"green\"],\"offset\":90,\"height\":50,\"width\":50},\"width\":50,\"height\":50},\"evals\":[],\"jsHooks\":[]}<\/script>","<span id=\"htmlwidget-0201c5b3295af0a92409\" class=\"sparkline html-widget\"><\/span>\n<script type=\"application/json\" data-for=\"htmlwidget-0201c5b3295af0a92409\">{\"x\":{\"values\":[2773,4750],\"options\":{\"type\":\"pie\",\"sliceColors\":[\"red\",\"green\"],\"offset\":90,\"height\":50,\"width\":50},\"width\":50,\"height\":50},\"evals\":[],\"jsHooks\":[]}<\/script>","<span id=\"htmlwidget-8c7a70784025a3d767a4\" class=\"sparkline html-widget\"><\/span>\n<script type=\"application/json\" data-for=\"htmlwidget-8c7a70784025a3d767a4\">{\"x\":{\"values\":[2475,2122],\"options\":{\"type\":\"pie\",\"sliceColors\":[\"red\",\"green\"],\"offset\":90,\"height\":50,\"width\":50},\"width\":50,\"height\":50},\"evals\":[],\"jsHooks\":[]}<\/script>","<span id=\"htmlwidget-2a48001d137dc3b20cdf\" class=\"sparkline html-widget\"><\/span>\n<script type=\"application/json\" data-for=\"htmlwidget-2a48001d137dc3b20cdf\">{\"x\":{\"values\":[4280,3293],\"options\":{\"type\":\"pie\",\"sliceColors\":[\"red\",\"green\"],\"offset\":90,\"height\":50,\"width\":50},\"width\":50,\"height\":50},\"evals\":[],\"jsHooks\":[]}<\/script>","<span id=\"htmlwidget-660ad2573abf9d4511c5\" class=\"sparkline html-widget\"><\/span>\n<script type=\"application/json\" data-for=\"htmlwidget-660ad2573abf9d4511c5\">{\"x\":{\"values\":[3271,3521],\"options\":{\"type\":\"pie\",\"sliceColors\":[\"red\",\"green\"],\"offset\":90,\"height\":50,\"width\":50},\"width\":50,\"height\":50},\"evals\":[],\"jsHooks\":[]}<\/script>","<span id=\"htmlwidget-88aa2e2790cc91e5c53b\" class=\"sparkline html-widget\"><\/span>\n<script type=\"application/json\" data-for=\"htmlwidget-88aa2e2790cc91e5c53b\">{\"x\":{\"values\":[2950,4159],\"options\":{\"type\":\"pie\",\"sliceColors\":[\"red\",\"green\"],\"offset\":90,\"height\":50,\"width\":50},\"width\":50,\"height\":50},\"evals\":[],\"jsHooks\":[]}<\/script>","<span id=\"htmlwidget-aa86bec20d424189e878\" class=\"sparkline html-widget\"><\/span>\n<script type=\"application/json\" data-for=\"htmlwidget-aa86bec20d424189e878\">{\"x\":{\"values\":[4517,3988],\"options\":{\"type\":\"pie\",\"sliceColors\":[\"red\",\"green\"],\"offset\":90,\"height\":50,\"width\":50},\"width\":50,\"height\":50},\"evals\":[],\"jsHooks\":[]}<\/script>","<span id=\"htmlwidget-1de1ceb67c60105c70e1\" class=\"sparkline html-widget\"><\/span>\n<script type=\"application/json\" data-for=\"htmlwidget-1de1ceb67c60105c70e1\">{\"x\":{\"values\":[2512,2799],\"options\":{\"type\":\"pie\",\"sliceColors\":[\"red\",\"green\"],\"offset\":90,\"height\":50,\"width\":50},\"width\":50,\"height\":50},\"evals\":[],\"jsHooks\":[]}<\/script>","<span id=\"htmlwidget-2cb3cea6a39644927c68\" class=\"sparkline html-widget\"><\/span>\n<script type=\"application/json\" data-for=\"htmlwidget-2cb3cea6a39644927c68\">{\"x\":{\"values\":[4496,4425],\"options\":{\"type\":\"pie\",\"sliceColors\":[\"red\",\"green\"],\"offset\":90,\"height\":50,\"width\":50},\"width\":50,\"height\":50},\"evals\":[],\"jsHooks\":[]}<\/script>","<span id=\"htmlwidget-38d6d5b1e5d72146e7d1\" class=\"sparkline html-widget\"><\/span>\n<script type=\"application/json\" data-for=\"htmlwidget-38d6d5b1e5d72146e7d1\">{\"x\":{\"values\":[4716,3547],\"options\":{\"type\":\"pie\",\"sliceColors\":[\"red\",\"green\"],\"offset\":90,\"height\":50,\"width\":50},\"width\":50,\"height\":50},\"evals\":[],\"jsHooks\":[]}<\/script>","<span id=\"htmlwidget-1a87e32318918e545976\" class=\"sparkline html-widget\"><\/span>\n<script type=\"application/json\" data-for=\"htmlwidget-1a87e32318918e545976\">{\"x\":{\"values\":[3998,2827],\"options\":{\"type\":\"pie\",\"sliceColors\":[\"red\",\"green\"],\"offset\":90,\"height\":50,\"width\":50},\"width\":50,\"height\":50},\"evals\":[],\"jsHooks\":[]}<\/script>","<span id=\"htmlwidget-255dbed7b553d147b084\" class=\"sparkline html-widget\"><\/span>\n<script type=\"application/json\" data-for=\"htmlwidget-255dbed7b553d147b084\">{\"x\":{\"values\":[2427,3989],\"options\":{\"type\":\"pie\",\"sliceColors\":[\"red\",\"green\"],\"offset\":90,\"height\":50,\"width\":50},\"width\":50,\"height\":50},\"evals\":[],\"jsHooks\":[]}<\/script>","<span id=\"htmlwidget-5702fa0563d6050d42f2\" class=\"sparkline html-widget\"><\/span>\n<script type=\"application/json\" data-for=\"htmlwidget-5702fa0563d6050d42f2\">{\"x\":{\"values\":[2358,4197],\"options\":{\"type\":\"pie\",\"sliceColors\":[\"red\",\"green\"],\"offset\":90,\"height\":50,\"width\":50},\"width\":50,\"height\":50},\"evals\":[],\"jsHooks\":[]}<\/script>","<span id=\"htmlwidget-c38ebd9c087492968971\" class=\"sparkline html-widget\"><\/span>\n<script type=\"application/json\" data-for=\"htmlwidget-c38ebd9c087492968971\">{\"x\":{\"values\":[2987,3130],\"options\":{\"type\":\"pie\",\"sliceColors\":[\"red\",\"green\"],\"offset\":90,\"height\":50,\"width\":50},\"width\":50,\"height\":50},\"evals\":[],\"jsHooks\":[]}<\/script>","<span id=\"htmlwidget-d5f811d5a0c42573aaaa\" class=\"sparkline html-widget\"><\/span>\n<script type=\"application/json\" data-for=\"htmlwidget-d5f811d5a0c42573aaaa\">{\"x\":{\"values\":[2275,3597],\"options\":{\"type\":\"pie\",\"sliceColors\":[\"red\",\"green\"],\"offset\":90,\"height\":50,\"width\":50},\"width\":50,\"height\":50},\"evals\":[],\"jsHooks\":[]}<\/script>","<span id=\"htmlwidget-42ae2ae88893191dbf04\" class=\"sparkline html-widget\"><\/span>\n<script type=\"application/json\" data-for=\"htmlwidget-42ae2ae88893191dbf04\">{\"x\":{\"values\":[3607,4499],\"options\":{\"type\":\"pie\",\"sliceColors\":[\"red\",\"green\"],\"offset\":90,\"height\":50,\"width\":50},\"width\":50,\"height\":50},\"evals\":[],\"jsHooks\":[]}<\/script>","<span id=\"htmlwidget-9bfd24d66144feee1c8b\" class=\"sparkline html-widget\"><\/span>\n<script type=\"application/json\" data-for=\"htmlwidget-9bfd24d66144feee1c8b\">{\"x\":{\"values\":[2796,2193],\"options\":{\"type\":\"pie\",\"sliceColors\":[\"red\",\"green\"],\"offset\":90,\"height\":50,\"width\":50},\"width\":50,\"height\":50},\"evals\":[],\"jsHooks\":[]}<\/script>","<span id=\"htmlwidget-601a8c353354eb071631\" class=\"sparkline html-widget\"><\/span>\n<script type=\"application/json\" data-for=\"htmlwidget-601a8c353354eb071631\">{\"x\":{\"values\":[4631,2492],\"options\":{\"type\":\"pie\",\"sliceColors\":[\"red\",\"green\"],\"offset\":90,\"height\":50,\"width\":50},\"width\":50,\"height\":50},\"evals\":[],\"jsHooks\":[]}<\/script>","<span id=\"htmlwidget-38d032ad728e4f5e6a17\" class=\"sparkline html-widget\"><\/span>\n<script type=\"application/json\" data-for=\"htmlwidget-38d032ad728e4f5e6a17\">{\"x\":{\"values\":[4303,2233],\"options\":{\"type\":\"pie\",\"sliceColors\":[\"red\",\"green\"],\"offset\":90,\"height\":50,\"width\":50},\"width\":50,\"height\":50},\"evals\":[],\"jsHooks\":[]}<\/script>"]],"container":"<table class=\"display\">\n  <thead>\n    <tr>\n      <th> <\/th>\n      <th>type1<\/th>\n      <th>sparkline1<\/th>\n    <\/tr>\n  <\/thead>\n<\/table>","options":{"pageLength":5,"dom":"tip","drawCallback":"function(s) { HTMLWidgets.staticRender(); }","columnDefs":[{"orderable":false,"targets":0}],"order":[],"autoWidth":false,"orderClasses":false,"lengthMenu":[5,10,25,50,100]}},"evals":["options.drawCallback"],"jsHooks":[]}</script>

### 1.7.3.组合图

为目标列引入一个迷你图时，用一个`sparkline()`函数，引入多组迷你图时，需要在`spk_composite()`函数中写入多个`sparkline()`来实现。

-   两条折线。

``` r
dt.DT <- dt[, .("两条折线"=as.character(htmltools::as.tags(spk_composite(
  sparkline(
    prob1,
    type = "line",
    fillColor = FALSE,
    lineColor = 'red', # 指定折线的颜色
    width = 200,
    height = 100
  ),
  sparkline(
    prob2,
    type = "line",
    fillColor = FALSE,
    lineColor = 'green',
    width = 200,
    height = 100
  )
)))), keyby = .(type2)]

datatable(dt.DT, escape = FALSE) |> spk_add_deps()
```

<div id="htmlwidget-48" style="width:100%;height:auto;" class="datatables html-widget"></div>
<script type="application/json" data-for="htmlwidget-48">{"x":{"filter":"none","vertical":false,"data":[["1","2"],["NO","YES"],["<span id=\"htmlwidget-febe7695b03ca8b22b78\" class=\"sparkline html-widget\"><\/span>\n<script type=\"application/json\" data-for=\"htmlwidget-febe7695b03ca8b22b78\">{\"x\":{\"values\":[0.39,0.19,0.54,0.04,0.47,0.69,0.46,0.26,0.86,0.22,0.63,0.89,0.94,0.95,0.01,0.32,0.07,0.13,0.85,0.31],\"options\":{\"type\":\"line\",\"fillColor\":false,\"lineColor\":\"red\",\"height\":100,\"width\":200},\"width\":200,\"height\":100,\"composites\":[{\"values\":[-0.02,0.28,0.32,-0.5,0.27,-0.11,-0.06,0.15,0.42,-0.16,0.18,0.05,0.43,-0.46,-0.14,0.16,-0.32,0.26,-0.13,-0.09],\"options\":{\"type\":\"line\",\"fillColor\":false,\"lineColor\":\"green\",\"height\":100,\"width\":200,\"composite\":true}}]},\"evals\":[],\"jsHooks\":[]}<\/script>","<span id=\"htmlwidget-eb602360ff32d9f9dc60\" class=\"sparkline html-widget\"><\/span>\n<script type=\"application/json\" data-for=\"htmlwidget-eb602360ff32d9f9dc60\">{\"x\":{\"values\":[0.02,0.29,0.03,0.36,0.38,0.65,0.2,0.77,0.59,0.34,0.83,0.42,0.45,0.58,0.28,0.96,0.76,0.05,0.75,0.23],\"options\":{\"type\":\"line\",\"fillColor\":false,\"lineColor\":\"red\",\"height\":100,\"width\":200},\"width\":200,\"height\":100,\"composites\":[{\"values\":[0.01,0.12,0,-0.01,0.24,-0.4,0.31,0.41,-0.05,-0.48,-0.45,0.02,0.04,-0.25,0.37,-0.34,0.44,-0.43,-0.42,-0.2],\"options\":{\"type\":\"line\",\"fillColor\":false,\"lineColor\":\"green\",\"height\":100,\"width\":200,\"composite\":true}}]},\"evals\":[],\"jsHooks\":[]}<\/script>"]],"container":"<table class=\"display\">\n  <thead>\n    <tr>\n      <th> <\/th>\n      <th>type2<\/th>\n      <th>两条折线<\/th>\n    <\/tr>\n  <\/thead>\n<\/table>","options":{"pageLength":5,"dom":"ftip","columnDefs":[{"orderable":false,"targets":0}],"order":[],"autoWidth":false,"orderClasses":false,"lengthMenu":[5,10,25,50,100]}},"evals":[],"jsHooks":[]}</script>

-   折柱混合。需要注意的是，参数 width（宽度）对柱形图不起作用，需要通过修改参数 barWidth（单个柱子的宽度）和参数 barSpacing（柱子之间的空隙）来达到改变整个迷你图宽度的效果。

``` r
dt.DT <- dt[, .("折柱混合" = as.character(htmltools::as.tags(spk_composite(
  sparkline(
    value1,
    type = "bar",
    width = 100,
    height = 100
  ),
  sparkline(
    prob2,
    type = "line",
    fillColor = FALSE,
    lineColor = 'green',
    lineWidth = 1.5, # 指定折线的宽度
    width = 100,
    height = 100
  )
)))), keyby = .(type2)]

datatable(dt.DT, escape = FALSE) |> spk_add_deps()
```

<div id="htmlwidget-49" style="width:100%;height:auto;" class="datatables html-widget"></div>
<script type="application/json" data-for="htmlwidget-49">{"x":{"filter":"none","vertical":false,"data":[["1","2"],["NO","YES"],["<span id=\"htmlwidget-27d64b1e0f08f29d2504\" class=\"sparkline html-widget\"><\/span>\n<script type=\"application/json\" data-for=\"htmlwidget-27d64b1e0f08f29d2504\">{\"x\":{\"values\":[1134,1510,1224,1242,1529,1584,202,1726,1855,1834,987,798,550,1100,1777,543,1688,345,1420,1229],\"options\":{\"type\":\"bar\",\"height\":100,\"width\":100},\"width\":100,\"height\":100,\"composites\":[{\"values\":[-0.02,0.28,0.32,-0.5,0.27,-0.11,-0.06,0.15,0.42,-0.16,0.18,0.05,0.43,-0.46,-0.14,0.16,-0.32,0.26,-0.13,-0.09],\"options\":{\"type\":\"line\",\"fillColor\":false,\"lineColor\":\"green\",\"lineWidth\":1.5,\"height\":100,\"width\":100,\"composite\":true}}]},\"evals\":[],\"jsHooks\":[]}<\/script>","<span id=\"htmlwidget-7479c39c668a66995f9e\" class=\"sparkline html-widget\"><\/span>\n<script type=\"application/json\" data-for=\"htmlwidget-7479c39c668a66995f9e\">{\"x\":{\"values\":[1576,1279,581,700,624,1471,1211,1255,616,1953,1441,1542,1715,1047,1929,735,1683,1601,1333,958],\"options\":{\"type\":\"bar\",\"height\":100,\"width\":100},\"width\":100,\"height\":100,\"composites\":[{\"values\":[0.01,0.12,0,-0.01,0.24,-0.4,0.31,0.41,-0.05,-0.48,-0.45,0.02,0.04,-0.25,0.37,-0.34,0.44,-0.43,-0.42,-0.2],\"options\":{\"type\":\"line\",\"fillColor\":false,\"lineColor\":\"green\",\"lineWidth\":1.5,\"height\":100,\"width\":100,\"composite\":true}}]},\"evals\":[],\"jsHooks\":[]}<\/script>"]],"container":"<table class=\"display\">\n  <thead>\n    <tr>\n      <th> <\/th>\n      <th>type2<\/th>\n      <th>折柱混合<\/th>\n    <\/tr>\n  <\/thead>\n<\/table>","options":{"pageLength":5,"dom":"ftip","columnDefs":[{"orderable":false,"targets":0}],"order":[],"autoWidth":false,"orderClasses":false,"lengthMenu":[5,10,25,50,100]}},"evals":[],"jsHooks":[]}</script>

## 1.8.样式冲突问题

DT 包中可设置静态样式的方法较多，最好的情况是一次只用一种方法设置好所需全部样式，否则用不同方法设置的同类样式之间会互相冲突。

| 序号 |      方法       | 所属章节 |                                                 描述                                                 |                                                       范围                                                       |                  限制                  |
|:----:|:---------------:|:--------:|:----------------------------------------------------------------------------------------------------:|:----------------------------------------------------------------------------------------------------------------:|:--------------------------------------:|
|  1   |    htmltools    | 第1.2节  |                                       在构建表格元素时设置样式                                       |                                    可为标题、脚注、表头等表格元素设定统一样式                                    | 无法为表格主体中单独几列或几行设定样式 |
|  2   | class/className | 第1.3节  | 先定义好 css 样式和类名，在`columnDefs = list(list(targets = null, class = '类名'))`中引入自定义样式 |                       可为全表表头或表格主体设定样式，也可为单独几列的表头或单元格设定样式                       |   无法为标题、脚注或单独几行设定样式   |
|  3   | `formatStyle()` | 第1.4节  |                    在 formatStyle 函数中直接一项一项地写入需要设定的 css 样式属性                    |                                      可对表格主体中的目标列或目标行设定样式                                      |     无法为标题、脚注或表头设定样式     |
|  4   |     `JS()`      | 第1.5节  |                     通过各种回调函数引入 JS 函数，在此基础上任意调用 html 或 css                     | 可对全表的表头、表格主体设置样式，也可对单列的表头、单元格设定样式，也可通过列渲染或行渲染对表格的行或列设置样式 |        无法为标题、脚注设定样式        |

### 1.8.1.多种方法混合使用时

如下，先设置一个样式名称为 class1，表示字体颜色为红色。

``` css
.class1{
 color: red;
}
```

<style type="text/css">
.class1{
 color: red;
}
</style>

其一，对比序号2和序号4对应的方法所产生的样式冲突表现。

-   在表格选项中设置初始化回调函数 `initComplete = JS()`，其中表头字体颜色均为粉色、表格主体字体颜色均为绿色。

-   在表格选项对列的定义 `columnDefs = list()` 里面，目标为第2列时，调用样式 class1。

-   在表格选项对列的定义 `columnDefs = list()` 里面，目标为第3列时，通过列渲染的方式，调用样式 class1。

显然，`initComplete = JS()` 设定的样式会被 `columnDefs = list()` 所覆盖。在后者之中，`list(targets = 2, class = 'class1')`会将该列的表头和单元格的字体颜色一并修改，而`list(targets = 3, render = JS())`仅修改了该列单元格的字体颜色，没有改变该列表头的字体颜色。

``` r
datatable(data, 
          options = list(
            initComplete = JS(
              "function(settings, json) {
    $(this.api().tables().body()).css({'color': 'green'});
    $(this.api().tables().header()).css({'color': 'pink'});
    }"
            ),
    columnDefs = list(list(targets = 2, class = 'class1'),
                      list(
                        targets = 3,
                        render = JS(
                          "function(data, type, row, meta){
              return '<div class=\"class1\">' + data + '</div>'
              }"
                        ))
              )
          ))
```

<div id="htmlwidget-50" style="width:100%;height:auto;" class="datatables html-widget"></div>
<script type="application/json" data-for="htmlwidget-50">{"x":{"filter":"none","vertical":false,"data":[["1","2","3","4","5","6","7","8","9","10","11","12","13","14","15","16","17","18","19","20","21","22","23","24","25","26","27","28","29","30","31","32","33","34","35","36","37","38","39","40"],["A","A","B","B","C","C","D","D","E","E","F","F","G","G","H","H","I","I","J","J","K","K","L","L","M","M","N","N","O","O","P","P","Q","Q","R","R","S","S","T","T"],["NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES"],[2227,3458,4870,2707,2773,4750,2475,2122,4280,3293,3271,3521,2950,4159,4517,3988,2512,2799,4496,4425,4716,3547,3998,2827,2427,3989,2358,4197,2987,3130,2275,3597,3607,4499,2796,2193,4631,2492,4303,2233],[1134,1576,1510,1279,1224,581,1242,700,1529,624,1584,1471,202,1211,1726,1255,1855,616,1834,1953,987,1441,798,1542,550,1715,1100,1047,1777,1929,543,735,1688,1683,345,1601,1420,1333,1229,958],[1502,1327,1647,1188,1430,1768,806,1875,565,1024,528,1258,603,490,935,438,301,1751,1161,1276,1606,1665,376,783,1143,1560,1571,663,697,1596,726,1128,313,1410,1020,1444,1935,1816,1346,912],[0.39,0.02,0.19,0.29,0.54,0.03,0.04,0.36,0.47,0.38,0.69,0.65,0.46,0.2,0.26,0.77,0.86,0.59,0.22,0.34,0.63,0.83,0.89,0.42,0.94,0.45,0.95,0.58,0.01,0.28,0.32,0.96,0.07,0.76,0.13,0.05,0.85,0.75,0.31,0.23],[-0.02,0.01,0.28,0.12,0.32,0,-0.5,-0.01,0.27,0.24,-0.11,-0.4,-0.06,0.31,0.15,0.41,0.42,-0.05,-0.16,-0.48,0.18,-0.45,0.05,0.02,0.43,0.04,-0.46,-0.25,-0.14,0.37,0.16,-0.34,-0.32,0.44,0.26,-0.43,-0.13,-0.42,-0.09,-0.2]],"container":"<table class=\"display\">\n  <thead>\n    <tr>\n      <th> <\/th>\n      <th>type1<\/th>\n      <th>type2<\/th>\n      <th>value<\/th>\n      <th>value1<\/th>\n      <th>value2<\/th>\n      <th>prob1<\/th>\n      <th>prob2<\/th>\n    <\/tr>\n  <\/thead>\n<\/table>","options":{"pageLength":5,"dom":"ftip","initComplete":"function(settings, json) {\n    $(this.api().tables().body()).css({'color': 'green'});\n    $(this.api().tables().header()).css({'color': 'pink'});\n    }","columnDefs":[{"targets":2,"class":"class1"},{"targets":3,"render":"function(data, type, row, meta){\n              return '<div class=\"class1\">' + data + '<\/div>'\n              }"},{"className":"dt-right","targets":[3,4,5,6,7]},{"orderable":false,"targets":0}],"order":[],"autoWidth":false,"orderClasses":false,"lengthMenu":[5,10,25,50,100]}},"evals":["options.initComplete","options.columnDefs.1.render"],"jsHooks":[]}</script>

其二，在以上对比结果的基础上，加入序号3所对应的方法，进一步观察样式冲突表现。由于初始化回调函数 `initComplete = JS()`所设定的样式会被覆盖，因此以下内容中可以省略。

-   在 formatStyle 函数中，定义目标列为第2、3列时，字体颜色为蓝色。
-   在 formatStyle 函数中，定义目标列第4列时，在不同条件下有不同字体颜色。

显然，`formatStyle(columns = 2, color = 'blue'` 与 `list(targets = 2, class = 'class1')` 产生了冲突，前者仅能修改该列表格主体中单元格的字体颜色，而未能修改表格表头的颜色。而 formatStyle 函数中对第3、4列的字体颜色设定均未能覆盖 `list(targets = c(3, 4), render = JS())`。但这并不表明 formatStyle 函数中一切样式的优先级均低于 `render = JS()`。

``` r
datatable(data, options = list(columnDefs = list(
  list(targets = 2, class = 'class1'),
  list(
    targets = c(3, 4), 
    render = JS(
      "function(data, type, row, meta){
              return '<div class=\"class1\">' + data + '</div>'
              }"
    )
  )
))) |>
  formatStyle(columns = 2, color = 'blue') |>
  formatStyle(columns = 3, color = 'blue') |>
  formatStyle(
    columns = 4,
    target = 'cell',
    color = styleEqual(
      levels = c('YES', 'NO'),
      values = c('green', 'red')
    )
  )
```

<div id="htmlwidget-51" style="width:100%;height:auto;" class="datatables html-widget"></div>
<script type="application/json" data-for="htmlwidget-51">{"x":{"filter":"none","vertical":false,"data":[["1","2","3","4","5","6","7","8","9","10","11","12","13","14","15","16","17","18","19","20","21","22","23","24","25","26","27","28","29","30","31","32","33","34","35","36","37","38","39","40"],["A","A","B","B","C","C","D","D","E","E","F","F","G","G","H","H","I","I","J","J","K","K","L","L","M","M","N","N","O","O","P","P","Q","Q","R","R","S","S","T","T"],["NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES"],[2227,3458,4870,2707,2773,4750,2475,2122,4280,3293,3271,3521,2950,4159,4517,3988,2512,2799,4496,4425,4716,3547,3998,2827,2427,3989,2358,4197,2987,3130,2275,3597,3607,4499,2796,2193,4631,2492,4303,2233],[1134,1576,1510,1279,1224,581,1242,700,1529,624,1584,1471,202,1211,1726,1255,1855,616,1834,1953,987,1441,798,1542,550,1715,1100,1047,1777,1929,543,735,1688,1683,345,1601,1420,1333,1229,958],[1502,1327,1647,1188,1430,1768,806,1875,565,1024,528,1258,603,490,935,438,301,1751,1161,1276,1606,1665,376,783,1143,1560,1571,663,697,1596,726,1128,313,1410,1020,1444,1935,1816,1346,912],[0.39,0.02,0.19,0.29,0.54,0.03,0.04,0.36,0.47,0.38,0.69,0.65,0.46,0.2,0.26,0.77,0.86,0.59,0.22,0.34,0.63,0.83,0.89,0.42,0.94,0.45,0.95,0.58,0.01,0.28,0.32,0.96,0.07,0.76,0.13,0.05,0.85,0.75,0.31,0.23],[-0.02,0.01,0.28,0.12,0.32,0,-0.5,-0.01,0.27,0.24,-0.11,-0.4,-0.06,0.31,0.15,0.41,0.42,-0.05,-0.16,-0.48,0.18,-0.45,0.05,0.02,0.43,0.04,-0.46,-0.25,-0.14,0.37,0.16,-0.34,-0.32,0.44,0.26,-0.43,-0.13,-0.42,-0.09,-0.2]],"container":"<table class=\"display\">\n  <thead>\n    <tr>\n      <th> <\/th>\n      <th>type1<\/th>\n      <th>type2<\/th>\n      <th>value<\/th>\n      <th>value1<\/th>\n      <th>value2<\/th>\n      <th>prob1<\/th>\n      <th>prob2<\/th>\n    <\/tr>\n  <\/thead>\n<\/table>","options":{"pageLength":5,"dom":"ftip","columnDefs":[{"targets":2,"class":"class1"},{"targets":[3,4],"render":"function(data, type, row, meta){\n              return '<div class=\"class1\">' + data + '<\/div>'\n              }"},{"className":"dt-right","targets":[3,4,5,6,7]},{"orderable":false,"targets":0}],"order":[],"autoWidth":false,"orderClasses":false,"lengthMenu":[5,10,25,50,100],"rowCallback":"function(row, data, displayNum, displayIndex, dataIndex) {\nvar value=data[2]; $(this.api().cell(row, 2).node()).css({'color':'blue'});\nvar value=data[3]; $(this.api().cell(row, 3).node()).css({'color':'blue'});\nvar value=data[4]; $(this.api().cell(row, 4).node()).css({'color':value == \"YES\" ? \"green\" : value == \"NO\" ? \"red\" : null});\n}"}},"evals":["options.columnDefs.1.render","options.rowCallback"],"jsHooks":[]}</script>

以上只是略作试验和说明，实际应用中碰到的样式冲突问题更为复杂。如无必要，不要把几种方法混着使用。

### 1.8.2.与 DT 默认样式的冲突

已知，DT 包默认将数值类型的列的文本对齐方式设定为右对齐。参照第1.3.3小节和第1.4.5小节可知，序号2/3的方法可以改变表格的文本对齐方式。

按照序号4的方法，设置初始化回调函数 `initComplete = JS()`，无法改变表格的文本对齐方式。

``` r
datatable(data,
          options = list(
            initComplete = JS(
              "function(settings, json) {
    $(this.api().tables().body()).css({'text-align': 'center'});
    $(this.api().tables().header()).css({'text-align': 'center'});
    }"
            )
          ))
```

<div id="htmlwidget-52" style="width:100%;height:auto;" class="datatables html-widget"></div>
<script type="application/json" data-for="htmlwidget-52">{"x":{"filter":"none","vertical":false,"data":[["1","2","3","4","5","6","7","8","9","10","11","12","13","14","15","16","17","18","19","20","21","22","23","24","25","26","27","28","29","30","31","32","33","34","35","36","37","38","39","40"],["A","A","B","B","C","C","D","D","E","E","F","F","G","G","H","H","I","I","J","J","K","K","L","L","M","M","N","N","O","O","P","P","Q","Q","R","R","S","S","T","T"],["NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES"],[2227,3458,4870,2707,2773,4750,2475,2122,4280,3293,3271,3521,2950,4159,4517,3988,2512,2799,4496,4425,4716,3547,3998,2827,2427,3989,2358,4197,2987,3130,2275,3597,3607,4499,2796,2193,4631,2492,4303,2233],[1134,1576,1510,1279,1224,581,1242,700,1529,624,1584,1471,202,1211,1726,1255,1855,616,1834,1953,987,1441,798,1542,550,1715,1100,1047,1777,1929,543,735,1688,1683,345,1601,1420,1333,1229,958],[1502,1327,1647,1188,1430,1768,806,1875,565,1024,528,1258,603,490,935,438,301,1751,1161,1276,1606,1665,376,783,1143,1560,1571,663,697,1596,726,1128,313,1410,1020,1444,1935,1816,1346,912],[0.39,0.02,0.19,0.29,0.54,0.03,0.04,0.36,0.47,0.38,0.69,0.65,0.46,0.2,0.26,0.77,0.86,0.59,0.22,0.34,0.63,0.83,0.89,0.42,0.94,0.45,0.95,0.58,0.01,0.28,0.32,0.96,0.07,0.76,0.13,0.05,0.85,0.75,0.31,0.23],[-0.02,0.01,0.28,0.12,0.32,0,-0.5,-0.01,0.27,0.24,-0.11,-0.4,-0.06,0.31,0.15,0.41,0.42,-0.05,-0.16,-0.48,0.18,-0.45,0.05,0.02,0.43,0.04,-0.46,-0.25,-0.14,0.37,0.16,-0.34,-0.32,0.44,0.26,-0.43,-0.13,-0.42,-0.09,-0.2]],"container":"<table class=\"display\">\n  <thead>\n    <tr>\n      <th> <\/th>\n      <th>type1<\/th>\n      <th>type2<\/th>\n      <th>value<\/th>\n      <th>value1<\/th>\n      <th>value2<\/th>\n      <th>prob1<\/th>\n      <th>prob2<\/th>\n    <\/tr>\n  <\/thead>\n<\/table>","options":{"pageLength":5,"dom":"ftip","initComplete":"function(settings, json) {\n    $(this.api().tables().body()).css({'text-align': 'center'});\n    $(this.api().tables().header()).css({'text-align': 'center'});\n    }","columnDefs":[{"className":"dt-right","targets":[3,4,5,6,7]},{"orderable":false,"targets":0}],"order":[],"autoWidth":false,"orderClasses":false,"lengthMenu":[5,10,25,50,100]}},"evals":["options.initComplete"],"jsHooks":[]}</script>

如下，设定一个样式类 class2，表示文本对齐方式为居中。

``` css
.class2{
text-align: center;
}
```

<style type="text/css">
.class2{
text-align: center;
}
</style>

在初始化回调函数 `initComplete = JS()` 中，针对第3列的表头和单元格设置的文本居中方式均起作用，而 `render = JS()` 中引入的样式无法对目标列的表头起作用。

``` r
datatable(data,
          options = list(
            initComplete = JS(
              "function(settings, json) {
    $(this.api().column(3).header()).css({'text-align': 'center'});
     $(this.api().column(3).nodes()).css({'text-align': 'center'});
    }"),
    columnDefs = list(list(
      targets = 4,
      render = JS(
        "function(data, type, row, meta){
              return '<div class=\"class2\">' + data + '</div>'
              }")))))
```

<div id="htmlwidget-53" style="width:100%;height:auto;" class="datatables html-widget"></div>
<script type="application/json" data-for="htmlwidget-53">{"x":{"filter":"none","vertical":false,"data":[["1","2","3","4","5","6","7","8","9","10","11","12","13","14","15","16","17","18","19","20","21","22","23","24","25","26","27","28","29","30","31","32","33","34","35","36","37","38","39","40"],["A","A","B","B","C","C","D","D","E","E","F","F","G","G","H","H","I","I","J","J","K","K","L","L","M","M","N","N","O","O","P","P","Q","Q","R","R","S","S","T","T"],["NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES"],[2227,3458,4870,2707,2773,4750,2475,2122,4280,3293,3271,3521,2950,4159,4517,3988,2512,2799,4496,4425,4716,3547,3998,2827,2427,3989,2358,4197,2987,3130,2275,3597,3607,4499,2796,2193,4631,2492,4303,2233],[1134,1576,1510,1279,1224,581,1242,700,1529,624,1584,1471,202,1211,1726,1255,1855,616,1834,1953,987,1441,798,1542,550,1715,1100,1047,1777,1929,543,735,1688,1683,345,1601,1420,1333,1229,958],[1502,1327,1647,1188,1430,1768,806,1875,565,1024,528,1258,603,490,935,438,301,1751,1161,1276,1606,1665,376,783,1143,1560,1571,663,697,1596,726,1128,313,1410,1020,1444,1935,1816,1346,912],[0.39,0.02,0.19,0.29,0.54,0.03,0.04,0.36,0.47,0.38,0.69,0.65,0.46,0.2,0.26,0.77,0.86,0.59,0.22,0.34,0.63,0.83,0.89,0.42,0.94,0.45,0.95,0.58,0.01,0.28,0.32,0.96,0.07,0.76,0.13,0.05,0.85,0.75,0.31,0.23],[-0.02,0.01,0.28,0.12,0.32,0,-0.5,-0.01,0.27,0.24,-0.11,-0.4,-0.06,0.31,0.15,0.41,0.42,-0.05,-0.16,-0.48,0.18,-0.45,0.05,0.02,0.43,0.04,-0.46,-0.25,-0.14,0.37,0.16,-0.34,-0.32,0.44,0.26,-0.43,-0.13,-0.42,-0.09,-0.2]],"container":"<table class=\"display\">\n  <thead>\n    <tr>\n      <th> <\/th>\n      <th>type1<\/th>\n      <th>type2<\/th>\n      <th>value<\/th>\n      <th>value1<\/th>\n      <th>value2<\/th>\n      <th>prob1<\/th>\n      <th>prob2<\/th>\n    <\/tr>\n  <\/thead>\n<\/table>","options":{"pageLength":5,"dom":"ftip","initComplete":"function(settings, json) {\n    $(this.api().column(3).header()).css({'text-align': 'center'});\n     $(this.api().column(3).nodes()).css({'text-align': 'center'});\n    }","columnDefs":[{"targets":4,"render":"function(data, type, row, meta){\n              return '<div class=\"class2\">' + data + '<\/div>'\n              }"},{"className":"dt-right","targets":[3,4,5,6,7]},{"orderable":false,"targets":0}],"order":[],"autoWidth":false,"orderClasses":false,"lengthMenu":[5,10,25,50,100]}},"evals":["options.initComplete","options.columnDefs.0.render"],"jsHooks":[]}</script>

# 第二章 动态效果

## 2.1.表格控件（dom）

DataTables 中有一些[表格控件](https://datatables.net/reference/option/dom)，可用于控制表格的动态元素。这些表格控件是否需要显示，其对应的位置和基础 css 样式都可以单独设置。

-   ‘l’：length，控制表格一页展示多少条记录
-   ‘f’：filtering，表格的筛选框，用于输入过滤条件
-   ‘t’：table，表格主体
-   ‘i’：information，展示表格基础信息汇总的内容，比如表中总记录数等
-   ‘p’：pagination，控制表格翻页
-   ‘r’：processing，加载时显示的内容

默认情况下，以上字母代表的表格控件全都应用，相当于`dom = 'lftipr'`，在设置`dom`参数时去掉某个字母便去掉了对应的表格控件，改变字母的顺序便改变了对应的表格控件出现的位置和顺序。

``` r
datatable(data, options = list(dom = 'ptfl'))
```

<div id="htmlwidget-54" style="width:100%;height:auto;" class="datatables html-widget"></div>
<script type="application/json" data-for="htmlwidget-54">{"x":{"filter":"none","vertical":false,"data":[["1","2","3","4","5","6","7","8","9","10","11","12","13","14","15","16","17","18","19","20","21","22","23","24","25","26","27","28","29","30","31","32","33","34","35","36","37","38","39","40"],["A","A","B","B","C","C","D","D","E","E","F","F","G","G","H","H","I","I","J","J","K","K","L","L","M","M","N","N","O","O","P","P","Q","Q","R","R","S","S","T","T"],["NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES"],[2227,3458,4870,2707,2773,4750,2475,2122,4280,3293,3271,3521,2950,4159,4517,3988,2512,2799,4496,4425,4716,3547,3998,2827,2427,3989,2358,4197,2987,3130,2275,3597,3607,4499,2796,2193,4631,2492,4303,2233],[1134,1576,1510,1279,1224,581,1242,700,1529,624,1584,1471,202,1211,1726,1255,1855,616,1834,1953,987,1441,798,1542,550,1715,1100,1047,1777,1929,543,735,1688,1683,345,1601,1420,1333,1229,958],[1502,1327,1647,1188,1430,1768,806,1875,565,1024,528,1258,603,490,935,438,301,1751,1161,1276,1606,1665,376,783,1143,1560,1571,663,697,1596,726,1128,313,1410,1020,1444,1935,1816,1346,912],[0.39,0.02,0.19,0.29,0.54,0.03,0.04,0.36,0.47,0.38,0.69,0.65,0.46,0.2,0.26,0.77,0.86,0.59,0.22,0.34,0.63,0.83,0.89,0.42,0.94,0.45,0.95,0.58,0.01,0.28,0.32,0.96,0.07,0.76,0.13,0.05,0.85,0.75,0.31,0.23],[-0.02,0.01,0.28,0.12,0.32,0,-0.5,-0.01,0.27,0.24,-0.11,-0.4,-0.06,0.31,0.15,0.41,0.42,-0.05,-0.16,-0.48,0.18,-0.45,0.05,0.02,0.43,0.04,-0.46,-0.25,-0.14,0.37,0.16,-0.34,-0.32,0.44,0.26,-0.43,-0.13,-0.42,-0.09,-0.2]],"container":"<table class=\"display\">\n  <thead>\n    <tr>\n      <th> <\/th>\n      <th>type1<\/th>\n      <th>type2<\/th>\n      <th>value<\/th>\n      <th>value1<\/th>\n      <th>value2<\/th>\n      <th>prob1<\/th>\n      <th>prob2<\/th>\n    <\/tr>\n  <\/thead>\n<\/table>","options":{"pageLength":5,"dom":"ptfl","columnDefs":[{"className":"dt-right","targets":[3,4,5,6,7]},{"orderable":false,"targets":0}],"order":[],"autoWidth":false,"orderClasses":false,"lengthMenu":[5,10,25,50,100]}},"evals":[],"jsHooks":[]}</script>

## 2.2.语言文字（language）

DataTables 中展示的语言文字选项都是可以修改的，详细参数见<https://datatables.net/reference/option/language>，下面列举了较为常见的几种。

-   info：此参数中有一些可随表格变动而动态更新的标记。
    -   `_START_`：当前页第一条记录。
    -   `_END`：当前页最后一条记录。
    -   `_TOTAL_`：筛选后表中总记录数。
    -   `_MAX_`：表中总记录数。
    -   `_PAGE_`：当前页。
    -   `_PAGES_`：表中总页数。

``` r
datatable(data, options = list(
  language = list(
    lengthMenu = '展示 _MENU_ 每页记录数',
    search = '检索：',
    zeroRecords = '什么都没有找到',
    infoEmpty = '找不到记录',
    infoFiltered = '(从 _MAX_ 条数据中筛选)',
    info = '共 _TOTAL_ 条记录，从 _START_ 到 _END_',
    paginate = list(previous = '上一页', `next` = '下一页')
  ),
  lengthMenu = c(5, 12, 24)
))
```

<div id="htmlwidget-55" style="width:100%;height:auto;" class="datatables html-widget"></div>
<script type="application/json" data-for="htmlwidget-55">{"x":{"filter":"none","vertical":false,"data":[["1","2","3","4","5","6","7","8","9","10","11","12","13","14","15","16","17","18","19","20","21","22","23","24","25","26","27","28","29","30","31","32","33","34","35","36","37","38","39","40"],["A","A","B","B","C","C","D","D","E","E","F","F","G","G","H","H","I","I","J","J","K","K","L","L","M","M","N","N","O","O","P","P","Q","Q","R","R","S","S","T","T"],["NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES"],[2227,3458,4870,2707,2773,4750,2475,2122,4280,3293,3271,3521,2950,4159,4517,3988,2512,2799,4496,4425,4716,3547,3998,2827,2427,3989,2358,4197,2987,3130,2275,3597,3607,4499,2796,2193,4631,2492,4303,2233],[1134,1576,1510,1279,1224,581,1242,700,1529,624,1584,1471,202,1211,1726,1255,1855,616,1834,1953,987,1441,798,1542,550,1715,1100,1047,1777,1929,543,735,1688,1683,345,1601,1420,1333,1229,958],[1502,1327,1647,1188,1430,1768,806,1875,565,1024,528,1258,603,490,935,438,301,1751,1161,1276,1606,1665,376,783,1143,1560,1571,663,697,1596,726,1128,313,1410,1020,1444,1935,1816,1346,912],[0.39,0.02,0.19,0.29,0.54,0.03,0.04,0.36,0.47,0.38,0.69,0.65,0.46,0.2,0.26,0.77,0.86,0.59,0.22,0.34,0.63,0.83,0.89,0.42,0.94,0.45,0.95,0.58,0.01,0.28,0.32,0.96,0.07,0.76,0.13,0.05,0.85,0.75,0.31,0.23],[-0.02,0.01,0.28,0.12,0.32,0,-0.5,-0.01,0.27,0.24,-0.11,-0.4,-0.06,0.31,0.15,0.41,0.42,-0.05,-0.16,-0.48,0.18,-0.45,0.05,0.02,0.43,0.04,-0.46,-0.25,-0.14,0.37,0.16,-0.34,-0.32,0.44,0.26,-0.43,-0.13,-0.42,-0.09,-0.2]],"container":"<table class=\"display\">\n  <thead>\n    <tr>\n      <th> <\/th>\n      <th>type1<\/th>\n      <th>type2<\/th>\n      <th>value<\/th>\n      <th>value1<\/th>\n      <th>value2<\/th>\n      <th>prob1<\/th>\n      <th>prob2<\/th>\n    <\/tr>\n  <\/thead>\n<\/table>","options":{"pageLength":5,"dom":"ftip","language":{"lengthMenu":"展示 _MENU_ 每页记录数","search":"检索：","zeroRecords":"什么都没有找到","infoEmpty":"找不到记录","infoFiltered":"(从 _MAX_ 条数据中筛选)","info":"共 _TOTAL_ 条记录，从 _START_ 到 _END_","paginate":{"previous":"上一页","next":"下一页"}},"lengthMenu":[5,12,24],"columnDefs":[{"className":"dt-right","targets":[3,4,5,6,7]},{"orderable":false,"targets":0}],"order":[],"autoWidth":false,"orderClasses":false}},"evals":[],"jsHooks":[]}</script>

除了可以对逐项细节作单独修改以外，也可以使用官方提供的插件直接替换。

``` r
datatable(data, options = list(
  language = list(url = '//cdn.datatables.net/plug-ins/1.10.11/i18n/Chinese.json')
))
```

<div id="htmlwidget-56" style="width:100%;height:auto;" class="datatables html-widget"></div>
<script type="application/json" data-for="htmlwidget-56">{"x":{"filter":"none","vertical":false,"data":[["1","2","3","4","5","6","7","8","9","10","11","12","13","14","15","16","17","18","19","20","21","22","23","24","25","26","27","28","29","30","31","32","33","34","35","36","37","38","39","40"],["A","A","B","B","C","C","D","D","E","E","F","F","G","G","H","H","I","I","J","J","K","K","L","L","M","M","N","N","O","O","P","P","Q","Q","R","R","S","S","T","T"],["NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES"],[2227,3458,4870,2707,2773,4750,2475,2122,4280,3293,3271,3521,2950,4159,4517,3988,2512,2799,4496,4425,4716,3547,3998,2827,2427,3989,2358,4197,2987,3130,2275,3597,3607,4499,2796,2193,4631,2492,4303,2233],[1134,1576,1510,1279,1224,581,1242,700,1529,624,1584,1471,202,1211,1726,1255,1855,616,1834,1953,987,1441,798,1542,550,1715,1100,1047,1777,1929,543,735,1688,1683,345,1601,1420,1333,1229,958],[1502,1327,1647,1188,1430,1768,806,1875,565,1024,528,1258,603,490,935,438,301,1751,1161,1276,1606,1665,376,783,1143,1560,1571,663,697,1596,726,1128,313,1410,1020,1444,1935,1816,1346,912],[0.39,0.02,0.19,0.29,0.54,0.03,0.04,0.36,0.47,0.38,0.69,0.65,0.46,0.2,0.26,0.77,0.86,0.59,0.22,0.34,0.63,0.83,0.89,0.42,0.94,0.45,0.95,0.58,0.01,0.28,0.32,0.96,0.07,0.76,0.13,0.05,0.85,0.75,0.31,0.23],[-0.02,0.01,0.28,0.12,0.32,0,-0.5,-0.01,0.27,0.24,-0.11,-0.4,-0.06,0.31,0.15,0.41,0.42,-0.05,-0.16,-0.48,0.18,-0.45,0.05,0.02,0.43,0.04,-0.46,-0.25,-0.14,0.37,0.16,-0.34,-0.32,0.44,0.26,-0.43,-0.13,-0.42,-0.09,-0.2]],"container":"<table class=\"display\">\n  <thead>\n    <tr>\n      <th> <\/th>\n      <th>type1<\/th>\n      <th>type2<\/th>\n      <th>value<\/th>\n      <th>value1<\/th>\n      <th>value2<\/th>\n      <th>prob1<\/th>\n      <th>prob2<\/th>\n    <\/tr>\n  <\/thead>\n<\/table>","options":{"pageLength":5,"dom":"ftip","language":{"url":"//cdn.datatables.net/plug-ins/1.10.11/i18n/Chinese.json"},"columnDefs":[{"className":"dt-right","targets":[3,4,5,6,7]},{"orderable":false,"targets":0}],"order":[],"autoWidth":false,"orderClasses":false,"lengthMenu":[5,10,25,50,100]}},"evals":[],"jsHooks":[]}</script>

## 2.3.滚动条（scrollX/scrollY）

当一页表格的行数或列数太多无法全部展示时，可以设置滚动条。

-   设置横轴的滚动条。

``` r
datatable(data, width = '500px', options = list(scrollX = TRUE))
```

<div id="htmlwidget-57" style="width:500px;height:auto;" class="datatables html-widget"></div>
<script type="application/json" data-for="htmlwidget-57">{"x":{"filter":"none","vertical":false,"data":[["1","2","3","4","5","6","7","8","9","10","11","12","13","14","15","16","17","18","19","20","21","22","23","24","25","26","27","28","29","30","31","32","33","34","35","36","37","38","39","40"],["A","A","B","B","C","C","D","D","E","E","F","F","G","G","H","H","I","I","J","J","K","K","L","L","M","M","N","N","O","O","P","P","Q","Q","R","R","S","S","T","T"],["NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES"],[2227,3458,4870,2707,2773,4750,2475,2122,4280,3293,3271,3521,2950,4159,4517,3988,2512,2799,4496,4425,4716,3547,3998,2827,2427,3989,2358,4197,2987,3130,2275,3597,3607,4499,2796,2193,4631,2492,4303,2233],[1134,1576,1510,1279,1224,581,1242,700,1529,624,1584,1471,202,1211,1726,1255,1855,616,1834,1953,987,1441,798,1542,550,1715,1100,1047,1777,1929,543,735,1688,1683,345,1601,1420,1333,1229,958],[1502,1327,1647,1188,1430,1768,806,1875,565,1024,528,1258,603,490,935,438,301,1751,1161,1276,1606,1665,376,783,1143,1560,1571,663,697,1596,726,1128,313,1410,1020,1444,1935,1816,1346,912],[0.39,0.02,0.19,0.29,0.54,0.03,0.04,0.36,0.47,0.38,0.69,0.65,0.46,0.2,0.26,0.77,0.86,0.59,0.22,0.34,0.63,0.83,0.89,0.42,0.94,0.45,0.95,0.58,0.01,0.28,0.32,0.96,0.07,0.76,0.13,0.05,0.85,0.75,0.31,0.23],[-0.02,0.01,0.28,0.12,0.32,0,-0.5,-0.01,0.27,0.24,-0.11,-0.4,-0.06,0.31,0.15,0.41,0.42,-0.05,-0.16,-0.48,0.18,-0.45,0.05,0.02,0.43,0.04,-0.46,-0.25,-0.14,0.37,0.16,-0.34,-0.32,0.44,0.26,-0.43,-0.13,-0.42,-0.09,-0.2]],"container":"<table class=\"display\">\n  <thead>\n    <tr>\n      <th> <\/th>\n      <th>type1<\/th>\n      <th>type2<\/th>\n      <th>value<\/th>\n      <th>value1<\/th>\n      <th>value2<\/th>\n      <th>prob1<\/th>\n      <th>prob2<\/th>\n    <\/tr>\n  <\/thead>\n<\/table>","options":{"pageLength":5,"dom":"ftip","scrollX":true,"columnDefs":[{"className":"dt-right","targets":[3,4,5,6,7]},{"orderable":false,"targets":0}],"order":[],"autoWidth":false,"orderClasses":false,"lengthMenu":[5,10,25,50,100]}},"evals":[],"jsHooks":[]}</script>

-   设置纵轴的滚动条，即将表格的高度强制展示为指定高度。

``` r
datatable(data,
          options = list(
            pageLength = 7, #设定分页时每页展示7行数据
            scrollY = '200px',
            scrollCollapse = TRUE #页面行数有限时，允许降低表格高度
          ))
```

<div id="htmlwidget-58" style="width:100%;height:auto;" class="datatables html-widget"></div>
<script type="application/json" data-for="htmlwidget-58">{"x":{"filter":"none","vertical":false,"data":[["1","2","3","4","5","6","7","8","9","10","11","12","13","14","15","16","17","18","19","20","21","22","23","24","25","26","27","28","29","30","31","32","33","34","35","36","37","38","39","40"],["A","A","B","B","C","C","D","D","E","E","F","F","G","G","H","H","I","I","J","J","K","K","L","L","M","M","N","N","O","O","P","P","Q","Q","R","R","S","S","T","T"],["NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES"],[2227,3458,4870,2707,2773,4750,2475,2122,4280,3293,3271,3521,2950,4159,4517,3988,2512,2799,4496,4425,4716,3547,3998,2827,2427,3989,2358,4197,2987,3130,2275,3597,3607,4499,2796,2193,4631,2492,4303,2233],[1134,1576,1510,1279,1224,581,1242,700,1529,624,1584,1471,202,1211,1726,1255,1855,616,1834,1953,987,1441,798,1542,550,1715,1100,1047,1777,1929,543,735,1688,1683,345,1601,1420,1333,1229,958],[1502,1327,1647,1188,1430,1768,806,1875,565,1024,528,1258,603,490,935,438,301,1751,1161,1276,1606,1665,376,783,1143,1560,1571,663,697,1596,726,1128,313,1410,1020,1444,1935,1816,1346,912],[0.39,0.02,0.19,0.29,0.54,0.03,0.04,0.36,0.47,0.38,0.69,0.65,0.46,0.2,0.26,0.77,0.86,0.59,0.22,0.34,0.63,0.83,0.89,0.42,0.94,0.45,0.95,0.58,0.01,0.28,0.32,0.96,0.07,0.76,0.13,0.05,0.85,0.75,0.31,0.23],[-0.02,0.01,0.28,0.12,0.32,0,-0.5,-0.01,0.27,0.24,-0.11,-0.4,-0.06,0.31,0.15,0.41,0.42,-0.05,-0.16,-0.48,0.18,-0.45,0.05,0.02,0.43,0.04,-0.46,-0.25,-0.14,0.37,0.16,-0.34,-0.32,0.44,0.26,-0.43,-0.13,-0.42,-0.09,-0.2]],"container":"<table class=\"display\">\n  <thead>\n    <tr>\n      <th> <\/th>\n      <th>type1<\/th>\n      <th>type2<\/th>\n      <th>value<\/th>\n      <th>value1<\/th>\n      <th>value2<\/th>\n      <th>prob1<\/th>\n      <th>prob2<\/th>\n    <\/tr>\n  <\/thead>\n<\/table>","options":{"pageLength":7,"dom":"ftip","scrollY":"200px","scrollCollapse":true,"columnDefs":[{"className":"dt-right","targets":[3,4,5,6,7]},{"orderable":false,"targets":0}],"order":[],"autoWidth":false,"orderClasses":false,"lengthMenu":[7,10,25,50,100]}},"evals":[],"jsHooks":[]}</script>

## 2.4.筛选（search）

### 2.4.1.筛选框（filter）

在筛选框输入过滤条件进行筛选时，其筛选范围是整张表的所有内容。在数据量较大时，全表筛选的效率可能不高，于是也可以专门设置仅针对单列数据进行筛选的筛选框。

``` r
datatable(
  data,
  options = list(dom = 'tp',  # 不展示表格控件中的筛选框
                 columnDefs = list(list(
                   targets = c(1, 3), searchable = FALSE
                 ))),# 设置目标列禁止使用筛选
  filter = list(
    position = 'top', # 可选参数值有"none", "bottom", "top"
    clear = TRUE, # 是否展示在筛选框中输入过滤条件后的清除按钮
    plain = FALSE
  )
)
```

<div id="htmlwidget-59" style="width:100%;height:auto;" class="datatables html-widget"></div>
<script type="application/json" data-for="htmlwidget-59">{"x":{"filter":"top","vertical":false,"filterHTML":"<tr>\n  <td><\/td>\n  <td data-type=\"character\" style=\"vertical-align: top;\">\n    <div class=\"form-group has-feedback\" style=\"margin-bottom: auto;\">\n      <input type=\"search\" placeholder=\"All\" class=\"form-control\" style=\"width: 100%;\"/>\n      <span class=\"glyphicon glyphicon-remove-circle form-control-feedback\"><\/span>\n    <\/div>\n  <\/td>\n  <td data-type=\"character\" style=\"vertical-align: top;\">\n    <div class=\"form-group has-feedback\" style=\"margin-bottom: auto;\">\n      <input type=\"search\" placeholder=\"All\" class=\"form-control\" style=\"width: 100%;\"/>\n      <span class=\"glyphicon glyphicon-remove-circle form-control-feedback\"><\/span>\n    <\/div>\n  <\/td>\n  <td data-type=\"integer\" style=\"vertical-align: top;\">\n    <div class=\"form-group has-feedback\" style=\"margin-bottom: auto;\">\n      <input type=\"search\" placeholder=\"All\" class=\"form-control\" style=\"width: 100%;\"/>\n      <span class=\"glyphicon glyphicon-remove-circle form-control-feedback\"><\/span>\n    <\/div>\n    <div style=\"display: none;position: absolute;width: 200px;opacity: 1\">\n      <div data-min=\"2122\" data-max=\"4870\"><\/div>\n      <span style=\"float: left;\"><\/span>\n      <span style=\"float: right;\"><\/span>\n    <\/div>\n  <\/td>\n  <td data-type=\"integer\" style=\"vertical-align: top;\">\n    <div class=\"form-group has-feedback\" style=\"margin-bottom: auto;\">\n      <input type=\"search\" placeholder=\"All\" class=\"form-control\" style=\"width: 100%;\"/>\n      <span class=\"glyphicon glyphicon-remove-circle form-control-feedback\"><\/span>\n    <\/div>\n    <div style=\"display: none;position: absolute;width: 200px;opacity: 1\">\n      <div data-min=\"202\" data-max=\"1953\"><\/div>\n      <span style=\"float: left;\"><\/span>\n      <span style=\"float: right;\"><\/span>\n    <\/div>\n  <\/td>\n  <td data-type=\"integer\" style=\"vertical-align: top;\">\n    <div class=\"form-group has-feedback\" style=\"margin-bottom: auto;\">\n      <input type=\"search\" placeholder=\"All\" class=\"form-control\" style=\"width: 100%;\"/>\n      <span class=\"glyphicon glyphicon-remove-circle form-control-feedback\"><\/span>\n    <\/div>\n    <div style=\"display: none;position: absolute;width: 200px;opacity: 1\">\n      <div data-min=\"301\" data-max=\"1935\"><\/div>\n      <span style=\"float: left;\"><\/span>\n      <span style=\"float: right;\"><\/span>\n    <\/div>\n  <\/td>\n  <td data-type=\"number\" style=\"vertical-align: top;\">\n    <div class=\"form-group has-feedback\" style=\"margin-bottom: auto;\">\n      <input type=\"search\" placeholder=\"All\" class=\"form-control\" style=\"width: 100%;\"/>\n      <span class=\"glyphicon glyphicon-remove-circle form-control-feedback\"><\/span>\n    <\/div>\n    <div style=\"display: none;position: absolute;width: 200px;opacity: 1\">\n      <div data-min=\"0.01\" data-max=\"0.96\" data-scale=\"2\"><\/div>\n      <span style=\"float: left;\"><\/span>\n      <span style=\"float: right;\"><\/span>\n    <\/div>\n  <\/td>\n  <td data-type=\"number\" style=\"vertical-align: top;\">\n    <div class=\"form-group has-feedback\" style=\"margin-bottom: auto;\">\n      <input type=\"search\" placeholder=\"All\" class=\"form-control\" style=\"width: 100%;\"/>\n      <span class=\"glyphicon glyphicon-remove-circle form-control-feedback\"><\/span>\n    <\/div>\n    <div style=\"display: none;position: absolute;width: 200px;opacity: 1\">\n      <div data-min=\"-0.5\" data-max=\"0.44\" data-scale=\"2\"><\/div>\n      <span style=\"float: left;\"><\/span>\n      <span style=\"float: right;\"><\/span>\n    <\/div>\n  <\/td>\n<\/tr>","data":[["1","2","3","4","5","6","7","8","9","10","11","12","13","14","15","16","17","18","19","20","21","22","23","24","25","26","27","28","29","30","31","32","33","34","35","36","37","38","39","40"],["A","A","B","B","C","C","D","D","E","E","F","F","G","G","H","H","I","I","J","J","K","K","L","L","M","M","N","N","O","O","P","P","Q","Q","R","R","S","S","T","T"],["NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES"],[2227,3458,4870,2707,2773,4750,2475,2122,4280,3293,3271,3521,2950,4159,4517,3988,2512,2799,4496,4425,4716,3547,3998,2827,2427,3989,2358,4197,2987,3130,2275,3597,3607,4499,2796,2193,4631,2492,4303,2233],[1134,1576,1510,1279,1224,581,1242,700,1529,624,1584,1471,202,1211,1726,1255,1855,616,1834,1953,987,1441,798,1542,550,1715,1100,1047,1777,1929,543,735,1688,1683,345,1601,1420,1333,1229,958],[1502,1327,1647,1188,1430,1768,806,1875,565,1024,528,1258,603,490,935,438,301,1751,1161,1276,1606,1665,376,783,1143,1560,1571,663,697,1596,726,1128,313,1410,1020,1444,1935,1816,1346,912],[0.39,0.02,0.19,0.29,0.54,0.03,0.04,0.36,0.47,0.38,0.69,0.65,0.46,0.2,0.26,0.77,0.86,0.59,0.22,0.34,0.63,0.83,0.89,0.42,0.94,0.45,0.95,0.58,0.01,0.28,0.32,0.96,0.07,0.76,0.13,0.05,0.85,0.75,0.31,0.23],[-0.02,0.01,0.28,0.12,0.32,0,-0.5,-0.01,0.27,0.24,-0.11,-0.4,-0.06,0.31,0.15,0.41,0.42,-0.05,-0.16,-0.48,0.18,-0.45,0.05,0.02,0.43,0.04,-0.46,-0.25,-0.14,0.37,0.16,-0.34,-0.32,0.44,0.26,-0.43,-0.13,-0.42,-0.09,-0.2]],"container":"<table class=\"display\">\n  <thead>\n    <tr>\n      <th> <\/th>\n      <th>type1<\/th>\n      <th>type2<\/th>\n      <th>value<\/th>\n      <th>value1<\/th>\n      <th>value2<\/th>\n      <th>prob1<\/th>\n      <th>prob2<\/th>\n    <\/tr>\n  <\/thead>\n<\/table>","options":{"pageLength":5,"dom":"tp","columnDefs":[{"targets":[1,3],"searchable":false},{"className":"dt-right","targets":[3,4,5,6,7]},{"orderable":false,"targets":0}],"order":[],"autoWidth":false,"orderClasses":false,"orderCellsTop":true,"lengthMenu":[5,10,25,50,100]}},"evals":[],"jsHooks":[]}</script>

### 2.4.2.过滤条件（search）

DataTables 内置的筛选过滤功能会按照输入条件与表格中任何位置的内容进行匹配，但并不仅仅只是简单的字符串对比或匹配，而是允许输入多个字符串来匹配，也可以输入一些正则表达式。

-   初始化过滤条件。如下`search = '5 s'`所匹配的结果是过滤出来的每一行都同时包括“5”和“s”。

``` r
datatable(data,
          options = list(search = list(search = '5 s' #初始化过滤条件
          )))
```

<div id="htmlwidget-60" style="width:100%;height:auto;" class="datatables html-widget"></div>
<script type="application/json" data-for="htmlwidget-60">{"x":{"filter":"none","vertical":false,"data":[["1","2","3","4","5","6","7","8","9","10","11","12","13","14","15","16","17","18","19","20","21","22","23","24","25","26","27","28","29","30","31","32","33","34","35","36","37","38","39","40"],["A","A","B","B","C","C","D","D","E","E","F","F","G","G","H","H","I","I","J","J","K","K","L","L","M","M","N","N","O","O","P","P","Q","Q","R","R","S","S","T","T"],["NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES"],[2227,3458,4870,2707,2773,4750,2475,2122,4280,3293,3271,3521,2950,4159,4517,3988,2512,2799,4496,4425,4716,3547,3998,2827,2427,3989,2358,4197,2987,3130,2275,3597,3607,4499,2796,2193,4631,2492,4303,2233],[1134,1576,1510,1279,1224,581,1242,700,1529,624,1584,1471,202,1211,1726,1255,1855,616,1834,1953,987,1441,798,1542,550,1715,1100,1047,1777,1929,543,735,1688,1683,345,1601,1420,1333,1229,958],[1502,1327,1647,1188,1430,1768,806,1875,565,1024,528,1258,603,490,935,438,301,1751,1161,1276,1606,1665,376,783,1143,1560,1571,663,697,1596,726,1128,313,1410,1020,1444,1935,1816,1346,912],[0.39,0.02,0.19,0.29,0.54,0.03,0.04,0.36,0.47,0.38,0.69,0.65,0.46,0.2,0.26,0.77,0.86,0.59,0.22,0.34,0.63,0.83,0.89,0.42,0.94,0.45,0.95,0.58,0.01,0.28,0.32,0.96,0.07,0.76,0.13,0.05,0.85,0.75,0.31,0.23],[-0.02,0.01,0.28,0.12,0.32,0,-0.5,-0.01,0.27,0.24,-0.11,-0.4,-0.06,0.31,0.15,0.41,0.42,-0.05,-0.16,-0.48,0.18,-0.45,0.05,0.02,0.43,0.04,-0.46,-0.25,-0.14,0.37,0.16,-0.34,-0.32,0.44,0.26,-0.43,-0.13,-0.42,-0.09,-0.2]],"container":"<table class=\"display\">\n  <thead>\n    <tr>\n      <th> <\/th>\n      <th>type1<\/th>\n      <th>type2<\/th>\n      <th>value<\/th>\n      <th>value1<\/th>\n      <th>value2<\/th>\n      <th>prob1<\/th>\n      <th>prob2<\/th>\n    <\/tr>\n  <\/thead>\n<\/table>","options":{"pageLength":5,"dom":"ftip","search":{"search":"5 s"},"columnDefs":[{"className":"dt-right","targets":[3,4,5,6,7]},{"orderable":false,"targets":0}],"order":[],"autoWidth":false,"orderClasses":false,"lengthMenu":[5,10,25,50,100]}},"evals":[],"jsHooks":[]}</script>

-   区分大小写。一般情况下，默认不区分字母大小写，但也可以设置为区分大小写。

``` r
datatable(data,
          options = list(search = list(search = '5 s', #初始化过滤条件
                                       caseInsensitive = FALSE # 是否区分大小写
          )))
```

<div id="htmlwidget-61" style="width:100%;height:auto;" class="datatables html-widget"></div>
<script type="application/json" data-for="htmlwidget-61">{"x":{"filter":"none","vertical":false,"data":[["1","2","3","4","5","6","7","8","9","10","11","12","13","14","15","16","17","18","19","20","21","22","23","24","25","26","27","28","29","30","31","32","33","34","35","36","37","38","39","40"],["A","A","B","B","C","C","D","D","E","E","F","F","G","G","H","H","I","I","J","J","K","K","L","L","M","M","N","N","O","O","P","P","Q","Q","R","R","S","S","T","T"],["NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES"],[2227,3458,4870,2707,2773,4750,2475,2122,4280,3293,3271,3521,2950,4159,4517,3988,2512,2799,4496,4425,4716,3547,3998,2827,2427,3989,2358,4197,2987,3130,2275,3597,3607,4499,2796,2193,4631,2492,4303,2233],[1134,1576,1510,1279,1224,581,1242,700,1529,624,1584,1471,202,1211,1726,1255,1855,616,1834,1953,987,1441,798,1542,550,1715,1100,1047,1777,1929,543,735,1688,1683,345,1601,1420,1333,1229,958],[1502,1327,1647,1188,1430,1768,806,1875,565,1024,528,1258,603,490,935,438,301,1751,1161,1276,1606,1665,376,783,1143,1560,1571,663,697,1596,726,1128,313,1410,1020,1444,1935,1816,1346,912],[0.39,0.02,0.19,0.29,0.54,0.03,0.04,0.36,0.47,0.38,0.69,0.65,0.46,0.2,0.26,0.77,0.86,0.59,0.22,0.34,0.63,0.83,0.89,0.42,0.94,0.45,0.95,0.58,0.01,0.28,0.32,0.96,0.07,0.76,0.13,0.05,0.85,0.75,0.31,0.23],[-0.02,0.01,0.28,0.12,0.32,0,-0.5,-0.01,0.27,0.24,-0.11,-0.4,-0.06,0.31,0.15,0.41,0.42,-0.05,-0.16,-0.48,0.18,-0.45,0.05,0.02,0.43,0.04,-0.46,-0.25,-0.14,0.37,0.16,-0.34,-0.32,0.44,0.26,-0.43,-0.13,-0.42,-0.09,-0.2]],"container":"<table class=\"display\">\n  <thead>\n    <tr>\n      <th> <\/th>\n      <th>type1<\/th>\n      <th>type2<\/th>\n      <th>value<\/th>\n      <th>value1<\/th>\n      <th>value2<\/th>\n      <th>prob1<\/th>\n      <th>prob2<\/th>\n    <\/tr>\n  <\/thead>\n<\/table>","options":{"pageLength":5,"dom":"ftip","search":{"search":"5 s","caseInsensitive":false},"columnDefs":[{"className":"dt-right","targets":[3,4,5,6,7]},{"orderable":false,"targets":0}],"order":[],"autoWidth":false,"orderClasses":false,"lengthMenu":[5,10,25,50,100]}},"evals":[],"jsHooks":[]}</script>

-   使用正则表达式。regex 参数可用来设定是否允许在筛选时使用正则表达时，DataTables 中默认此参数值为 TRUE，而 DT 包中则默认此参数值为 FALSE，即筛选框默认无法使用正则表达式。

``` r
datatable(data,
          options = list(search = list(regex = TRUE, # 是否允许使用正则表达式
                                       search = '5[4|6] s' #初始化过滤条件
          )))
```

<div id="htmlwidget-62" style="width:100%;height:auto;" class="datatables html-widget"></div>
<script type="application/json" data-for="htmlwidget-62">{"x":{"filter":"none","vertical":false,"data":[["1","2","3","4","5","6","7","8","9","10","11","12","13","14","15","16","17","18","19","20","21","22","23","24","25","26","27","28","29","30","31","32","33","34","35","36","37","38","39","40"],["A","A","B","B","C","C","D","D","E","E","F","F","G","G","H","H","I","I","J","J","K","K","L","L","M","M","N","N","O","O","P","P","Q","Q","R","R","S","S","T","T"],["NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES"],[2227,3458,4870,2707,2773,4750,2475,2122,4280,3293,3271,3521,2950,4159,4517,3988,2512,2799,4496,4425,4716,3547,3998,2827,2427,3989,2358,4197,2987,3130,2275,3597,3607,4499,2796,2193,4631,2492,4303,2233],[1134,1576,1510,1279,1224,581,1242,700,1529,624,1584,1471,202,1211,1726,1255,1855,616,1834,1953,987,1441,798,1542,550,1715,1100,1047,1777,1929,543,735,1688,1683,345,1601,1420,1333,1229,958],[1502,1327,1647,1188,1430,1768,806,1875,565,1024,528,1258,603,490,935,438,301,1751,1161,1276,1606,1665,376,783,1143,1560,1571,663,697,1596,726,1128,313,1410,1020,1444,1935,1816,1346,912],[0.39,0.02,0.19,0.29,0.54,0.03,0.04,0.36,0.47,0.38,0.69,0.65,0.46,0.2,0.26,0.77,0.86,0.59,0.22,0.34,0.63,0.83,0.89,0.42,0.94,0.45,0.95,0.58,0.01,0.28,0.32,0.96,0.07,0.76,0.13,0.05,0.85,0.75,0.31,0.23],[-0.02,0.01,0.28,0.12,0.32,0,-0.5,-0.01,0.27,0.24,-0.11,-0.4,-0.06,0.31,0.15,0.41,0.42,-0.05,-0.16,-0.48,0.18,-0.45,0.05,0.02,0.43,0.04,-0.46,-0.25,-0.14,0.37,0.16,-0.34,-0.32,0.44,0.26,-0.43,-0.13,-0.42,-0.09,-0.2]],"container":"<table class=\"display\">\n  <thead>\n    <tr>\n      <th> <\/th>\n      <th>type1<\/th>\n      <th>type2<\/th>\n      <th>value<\/th>\n      <th>value1<\/th>\n      <th>value2<\/th>\n      <th>prob1<\/th>\n      <th>prob2<\/th>\n    <\/tr>\n  <\/thead>\n<\/table>","options":{"pageLength":5,"dom":"ftip","search":{"regex":true,"search":"5[4|6] s"},"columnDefs":[{"className":"dt-right","targets":[3,4,5,6,7]},{"orderable":false,"targets":0}],"order":[],"autoWidth":false,"orderClasses":false,"lengthMenu":[5,10,25,50,100]}},"evals":[],"jsHooks":[]}</script>

-   启用过滤条件。return 参数默认值为 FALSE，即当筛选框中输入内容后，对整个表格的过滤功能便实时启用。当设置为`return = TRUE`时，那么必须在筛选框中按下 Enter 键后，过滤功能才会启用，此项参数可能在应用大型数据集时非常有用。

``` r
datatable(data,
          options = list(search = list(regex = TRUE, # 是否允许使用正则表达式
                                       search = '5[4|6] s', #初始化过滤条件
                                       return = TRUE
          )))
```

<div id="htmlwidget-63" style="width:100%;height:auto;" class="datatables html-widget"></div>
<script type="application/json" data-for="htmlwidget-63">{"x":{"filter":"none","vertical":false,"data":[["1","2","3","4","5","6","7","8","9","10","11","12","13","14","15","16","17","18","19","20","21","22","23","24","25","26","27","28","29","30","31","32","33","34","35","36","37","38","39","40"],["A","A","B","B","C","C","D","D","E","E","F","F","G","G","H","H","I","I","J","J","K","K","L","L","M","M","N","N","O","O","P","P","Q","Q","R","R","S","S","T","T"],["NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES"],[2227,3458,4870,2707,2773,4750,2475,2122,4280,3293,3271,3521,2950,4159,4517,3988,2512,2799,4496,4425,4716,3547,3998,2827,2427,3989,2358,4197,2987,3130,2275,3597,3607,4499,2796,2193,4631,2492,4303,2233],[1134,1576,1510,1279,1224,581,1242,700,1529,624,1584,1471,202,1211,1726,1255,1855,616,1834,1953,987,1441,798,1542,550,1715,1100,1047,1777,1929,543,735,1688,1683,345,1601,1420,1333,1229,958],[1502,1327,1647,1188,1430,1768,806,1875,565,1024,528,1258,603,490,935,438,301,1751,1161,1276,1606,1665,376,783,1143,1560,1571,663,697,1596,726,1128,313,1410,1020,1444,1935,1816,1346,912],[0.39,0.02,0.19,0.29,0.54,0.03,0.04,0.36,0.47,0.38,0.69,0.65,0.46,0.2,0.26,0.77,0.86,0.59,0.22,0.34,0.63,0.83,0.89,0.42,0.94,0.45,0.95,0.58,0.01,0.28,0.32,0.96,0.07,0.76,0.13,0.05,0.85,0.75,0.31,0.23],[-0.02,0.01,0.28,0.12,0.32,0,-0.5,-0.01,0.27,0.24,-0.11,-0.4,-0.06,0.31,0.15,0.41,0.42,-0.05,-0.16,-0.48,0.18,-0.45,0.05,0.02,0.43,0.04,-0.46,-0.25,-0.14,0.37,0.16,-0.34,-0.32,0.44,0.26,-0.43,-0.13,-0.42,-0.09,-0.2]],"container":"<table class=\"display\">\n  <thead>\n    <tr>\n      <th> <\/th>\n      <th>type1<\/th>\n      <th>type2<\/th>\n      <th>value<\/th>\n      <th>value1<\/th>\n      <th>value2<\/th>\n      <th>prob1<\/th>\n      <th>prob2<\/th>\n    <\/tr>\n  <\/thead>\n<\/table>","options":{"pageLength":5,"dom":"ftip","search":{"regex":true,"search":"5[4|6] s","return":true},"columnDefs":[{"className":"dt-right","targets":[3,4,5,6,7]},{"orderable":false,"targets":0}],"order":[],"autoWidth":false,"orderClasses":false,"lengthMenu":[5,10,25,50,100]}},"evals":[],"jsHooks":[]}</script>

-   筛选结果高亮。全局筛选时，所有匹配内容均突出显示。

``` r
datatable(data, options = list(searchHighlight = TRUE, search = list(search = '5 s')))
```

<div id="htmlwidget-64" style="width:100%;height:auto;" class="datatables html-widget"></div>
<script type="application/json" data-for="htmlwidget-64">{"x":{"filter":"none","vertical":false,"data":[["1","2","3","4","5","6","7","8","9","10","11","12","13","14","15","16","17","18","19","20","21","22","23","24","25","26","27","28","29","30","31","32","33","34","35","36","37","38","39","40"],["A","A","B","B","C","C","D","D","E","E","F","F","G","G","H","H","I","I","J","J","K","K","L","L","M","M","N","N","O","O","P","P","Q","Q","R","R","S","S","T","T"],["NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES"],[2227,3458,4870,2707,2773,4750,2475,2122,4280,3293,3271,3521,2950,4159,4517,3988,2512,2799,4496,4425,4716,3547,3998,2827,2427,3989,2358,4197,2987,3130,2275,3597,3607,4499,2796,2193,4631,2492,4303,2233],[1134,1576,1510,1279,1224,581,1242,700,1529,624,1584,1471,202,1211,1726,1255,1855,616,1834,1953,987,1441,798,1542,550,1715,1100,1047,1777,1929,543,735,1688,1683,345,1601,1420,1333,1229,958],[1502,1327,1647,1188,1430,1768,806,1875,565,1024,528,1258,603,490,935,438,301,1751,1161,1276,1606,1665,376,783,1143,1560,1571,663,697,1596,726,1128,313,1410,1020,1444,1935,1816,1346,912],[0.39,0.02,0.19,0.29,0.54,0.03,0.04,0.36,0.47,0.38,0.69,0.65,0.46,0.2,0.26,0.77,0.86,0.59,0.22,0.34,0.63,0.83,0.89,0.42,0.94,0.45,0.95,0.58,0.01,0.28,0.32,0.96,0.07,0.76,0.13,0.05,0.85,0.75,0.31,0.23],[-0.02,0.01,0.28,0.12,0.32,0,-0.5,-0.01,0.27,0.24,-0.11,-0.4,-0.06,0.31,0.15,0.41,0.42,-0.05,-0.16,-0.48,0.18,-0.45,0.05,0.02,0.43,0.04,-0.46,-0.25,-0.14,0.37,0.16,-0.34,-0.32,0.44,0.26,-0.43,-0.13,-0.42,-0.09,-0.2]],"container":"<table class=\"display\">\n  <thead>\n    <tr>\n      <th> <\/th>\n      <th>type1<\/th>\n      <th>type2<\/th>\n      <th>value<\/th>\n      <th>value1<\/th>\n      <th>value2<\/th>\n      <th>prob1<\/th>\n      <th>prob2<\/th>\n    <\/tr>\n  <\/thead>\n<\/table>","options":{"pageLength":5,"dom":"ftip","searchHighlight":true,"search":{"search":"5 s"},"columnDefs":[{"className":"dt-right","targets":[3,4,5,6,7]},{"orderable":false,"targets":0}],"order":[],"autoWidth":false,"orderClasses":false,"lengthMenu":[5,10,25,50,100]}},"evals":[],"jsHooks":[]}</script>

仅对单列筛选时，只有字符列能突出显示。

``` r
datatable(data,
          options = list(
            searchHighlight = TRUE,
            search = list(targets = 2, search = 's')
          ),
          filter = 'top')
```

<div id="htmlwidget-65" style="width:100%;height:auto;" class="datatables html-widget"></div>
<script type="application/json" data-for="htmlwidget-65">{"x":{"filter":"top","vertical":false,"filterHTML":"<tr>\n  <td><\/td>\n  <td data-type=\"character\" style=\"vertical-align: top;\">\n    <div class=\"form-group has-feedback\" style=\"margin-bottom: auto;\">\n      <input type=\"search\" placeholder=\"All\" class=\"form-control\" style=\"width: 100%;\"/>\n      <span class=\"glyphicon glyphicon-remove-circle form-control-feedback\"><\/span>\n    <\/div>\n  <\/td>\n  <td data-type=\"character\" style=\"vertical-align: top;\">\n    <div class=\"form-group has-feedback\" style=\"margin-bottom: auto;\">\n      <input type=\"search\" placeholder=\"All\" class=\"form-control\" style=\"width: 100%;\"/>\n      <span class=\"glyphicon glyphicon-remove-circle form-control-feedback\"><\/span>\n    <\/div>\n  <\/td>\n  <td data-type=\"integer\" style=\"vertical-align: top;\">\n    <div class=\"form-group has-feedback\" style=\"margin-bottom: auto;\">\n      <input type=\"search\" placeholder=\"All\" class=\"form-control\" style=\"width: 100%;\"/>\n      <span class=\"glyphicon glyphicon-remove-circle form-control-feedback\"><\/span>\n    <\/div>\n    <div style=\"display: none;position: absolute;width: 200px;opacity: 1\">\n      <div data-min=\"2122\" data-max=\"4870\"><\/div>\n      <span style=\"float: left;\"><\/span>\n      <span style=\"float: right;\"><\/span>\n    <\/div>\n  <\/td>\n  <td data-type=\"integer\" style=\"vertical-align: top;\">\n    <div class=\"form-group has-feedback\" style=\"margin-bottom: auto;\">\n      <input type=\"search\" placeholder=\"All\" class=\"form-control\" style=\"width: 100%;\"/>\n      <span class=\"glyphicon glyphicon-remove-circle form-control-feedback\"><\/span>\n    <\/div>\n    <div style=\"display: none;position: absolute;width: 200px;opacity: 1\">\n      <div data-min=\"202\" data-max=\"1953\"><\/div>\n      <span style=\"float: left;\"><\/span>\n      <span style=\"float: right;\"><\/span>\n    <\/div>\n  <\/td>\n  <td data-type=\"integer\" style=\"vertical-align: top;\">\n    <div class=\"form-group has-feedback\" style=\"margin-bottom: auto;\">\n      <input type=\"search\" placeholder=\"All\" class=\"form-control\" style=\"width: 100%;\"/>\n      <span class=\"glyphicon glyphicon-remove-circle form-control-feedback\"><\/span>\n    <\/div>\n    <div style=\"display: none;position: absolute;width: 200px;opacity: 1\">\n      <div data-min=\"301\" data-max=\"1935\"><\/div>\n      <span style=\"float: left;\"><\/span>\n      <span style=\"float: right;\"><\/span>\n    <\/div>\n  <\/td>\n  <td data-type=\"number\" style=\"vertical-align: top;\">\n    <div class=\"form-group has-feedback\" style=\"margin-bottom: auto;\">\n      <input type=\"search\" placeholder=\"All\" class=\"form-control\" style=\"width: 100%;\"/>\n      <span class=\"glyphicon glyphicon-remove-circle form-control-feedback\"><\/span>\n    <\/div>\n    <div style=\"display: none;position: absolute;width: 200px;opacity: 1\">\n      <div data-min=\"0.01\" data-max=\"0.96\" data-scale=\"2\"><\/div>\n      <span style=\"float: left;\"><\/span>\n      <span style=\"float: right;\"><\/span>\n    <\/div>\n  <\/td>\n  <td data-type=\"number\" style=\"vertical-align: top;\">\n    <div class=\"form-group has-feedback\" style=\"margin-bottom: auto;\">\n      <input type=\"search\" placeholder=\"All\" class=\"form-control\" style=\"width: 100%;\"/>\n      <span class=\"glyphicon glyphicon-remove-circle form-control-feedback\"><\/span>\n    <\/div>\n    <div style=\"display: none;position: absolute;width: 200px;opacity: 1\">\n      <div data-min=\"-0.5\" data-max=\"0.44\" data-scale=\"2\"><\/div>\n      <span style=\"float: left;\"><\/span>\n      <span style=\"float: right;\"><\/span>\n    <\/div>\n  <\/td>\n<\/tr>","data":[["1","2","3","4","5","6","7","8","9","10","11","12","13","14","15","16","17","18","19","20","21","22","23","24","25","26","27","28","29","30","31","32","33","34","35","36","37","38","39","40"],["A","A","B","B","C","C","D","D","E","E","F","F","G","G","H","H","I","I","J","J","K","K","L","L","M","M","N","N","O","O","P","P","Q","Q","R","R","S","S","T","T"],["NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES"],[2227,3458,4870,2707,2773,4750,2475,2122,4280,3293,3271,3521,2950,4159,4517,3988,2512,2799,4496,4425,4716,3547,3998,2827,2427,3989,2358,4197,2987,3130,2275,3597,3607,4499,2796,2193,4631,2492,4303,2233],[1134,1576,1510,1279,1224,581,1242,700,1529,624,1584,1471,202,1211,1726,1255,1855,616,1834,1953,987,1441,798,1542,550,1715,1100,1047,1777,1929,543,735,1688,1683,345,1601,1420,1333,1229,958],[1502,1327,1647,1188,1430,1768,806,1875,565,1024,528,1258,603,490,935,438,301,1751,1161,1276,1606,1665,376,783,1143,1560,1571,663,697,1596,726,1128,313,1410,1020,1444,1935,1816,1346,912],[0.39,0.02,0.19,0.29,0.54,0.03,0.04,0.36,0.47,0.38,0.69,0.65,0.46,0.2,0.26,0.77,0.86,0.59,0.22,0.34,0.63,0.83,0.89,0.42,0.94,0.45,0.95,0.58,0.01,0.28,0.32,0.96,0.07,0.76,0.13,0.05,0.85,0.75,0.31,0.23],[-0.02,0.01,0.28,0.12,0.32,0,-0.5,-0.01,0.27,0.24,-0.11,-0.4,-0.06,0.31,0.15,0.41,0.42,-0.05,-0.16,-0.48,0.18,-0.45,0.05,0.02,0.43,0.04,-0.46,-0.25,-0.14,0.37,0.16,-0.34,-0.32,0.44,0.26,-0.43,-0.13,-0.42,-0.09,-0.2]],"container":"<table class=\"display\">\n  <thead>\n    <tr>\n      <th> <\/th>\n      <th>type1<\/th>\n      <th>type2<\/th>\n      <th>value<\/th>\n      <th>value1<\/th>\n      <th>value2<\/th>\n      <th>prob1<\/th>\n      <th>prob2<\/th>\n    <\/tr>\n  <\/thead>\n<\/table>","options":{"pageLength":5,"dom":"ftip","searchHighlight":true,"search":{"targets":2,"search":"s"},"columnDefs":[{"className":"dt-right","targets":[3,4,5,6,7]},{"orderable":false,"targets":0}],"order":[],"autoWidth":false,"orderClasses":false,"orderCellsTop":true,"lengthMenu":[5,10,25,50,100]}},"evals":[],"jsHooks":[]}</script>

## 2.5.排序（order）

<!--<https://datatables.net/reference/option/order>-->

### 2.5.1.列的排序方式（order）

order 参数可用来设置初始化的排序方式。在使用表格的过程中，各列表头处都有正三角和倒三角符号，分别表示正序和倒许，鼠标单击那些三角符号，便可以更改目标列的数据排序方式。

``` r
datatable(data, options = list(
  order = list(list(1, 'asc'), # 设置目标列升序
               list(2, 'desc') # 设置目标列降序
               ), 
  columnDefs = list(list(targets = 3,
                         orderable = FALSE # 禁止对目标列排序
                         ))))
```

<div id="htmlwidget-66" style="width:100%;height:auto;" class="datatables html-widget"></div>
<script type="application/json" data-for="htmlwidget-66">{"x":{"filter":"none","vertical":false,"data":[["1","2","3","4","5","6","7","8","9","10","11","12","13","14","15","16","17","18","19","20","21","22","23","24","25","26","27","28","29","30","31","32","33","34","35","36","37","38","39","40"],["A","A","B","B","C","C","D","D","E","E","F","F","G","G","H","H","I","I","J","J","K","K","L","L","M","M","N","N","O","O","P","P","Q","Q","R","R","S","S","T","T"],["NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES"],[2227,3458,4870,2707,2773,4750,2475,2122,4280,3293,3271,3521,2950,4159,4517,3988,2512,2799,4496,4425,4716,3547,3998,2827,2427,3989,2358,4197,2987,3130,2275,3597,3607,4499,2796,2193,4631,2492,4303,2233],[1134,1576,1510,1279,1224,581,1242,700,1529,624,1584,1471,202,1211,1726,1255,1855,616,1834,1953,987,1441,798,1542,550,1715,1100,1047,1777,1929,543,735,1688,1683,345,1601,1420,1333,1229,958],[1502,1327,1647,1188,1430,1768,806,1875,565,1024,528,1258,603,490,935,438,301,1751,1161,1276,1606,1665,376,783,1143,1560,1571,663,697,1596,726,1128,313,1410,1020,1444,1935,1816,1346,912],[0.39,0.02,0.19,0.29,0.54,0.03,0.04,0.36,0.47,0.38,0.69,0.65,0.46,0.2,0.26,0.77,0.86,0.59,0.22,0.34,0.63,0.83,0.89,0.42,0.94,0.45,0.95,0.58,0.01,0.28,0.32,0.96,0.07,0.76,0.13,0.05,0.85,0.75,0.31,0.23],[-0.02,0.01,0.28,0.12,0.32,0,-0.5,-0.01,0.27,0.24,-0.11,-0.4,-0.06,0.31,0.15,0.41,0.42,-0.05,-0.16,-0.48,0.18,-0.45,0.05,0.02,0.43,0.04,-0.46,-0.25,-0.14,0.37,0.16,-0.34,-0.32,0.44,0.26,-0.43,-0.13,-0.42,-0.09,-0.2]],"container":"<table class=\"display\">\n  <thead>\n    <tr>\n      <th> <\/th>\n      <th>type1<\/th>\n      <th>type2<\/th>\n      <th>value<\/th>\n      <th>value1<\/th>\n      <th>value2<\/th>\n      <th>prob1<\/th>\n      <th>prob2<\/th>\n    <\/tr>\n  <\/thead>\n<\/table>","options":{"pageLength":5,"dom":"ftip","order":[[1,"asc"],[2,"desc"]],"columnDefs":[{"targets":3,"orderable":false},{"className":"dt-right","targets":[3,4,5,6,7]},{"orderable":false,"targets":0}],"autoWidth":false,"orderClasses":false,"lengthMenu":[5,10,25,50,100]}},"evals":[],"jsHooks":[]}</script>

### 2.5.2.固定列的排序方式（orderFixed）

<!--<https://datatables.net/reference/option/orderFixed><https://datatables.net/reference/api/order.fixed()>-->

可以固定一列或多列的排序方式，即使某一列隐藏，该列排序效果仍然存在。

``` r
datatable(data, options = list(orderFixed = list(list(1, 'asc'), list(2, 'desc'))))
```

<div id="htmlwidget-67" style="width:100%;height:auto;" class="datatables html-widget"></div>
<script type="application/json" data-for="htmlwidget-67">{"x":{"filter":"none","vertical":false,"data":[["1","2","3","4","5","6","7","8","9","10","11","12","13","14","15","16","17","18","19","20","21","22","23","24","25","26","27","28","29","30","31","32","33","34","35","36","37","38","39","40"],["A","A","B","B","C","C","D","D","E","E","F","F","G","G","H","H","I","I","J","J","K","K","L","L","M","M","N","N","O","O","P","P","Q","Q","R","R","S","S","T","T"],["NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES"],[2227,3458,4870,2707,2773,4750,2475,2122,4280,3293,3271,3521,2950,4159,4517,3988,2512,2799,4496,4425,4716,3547,3998,2827,2427,3989,2358,4197,2987,3130,2275,3597,3607,4499,2796,2193,4631,2492,4303,2233],[1134,1576,1510,1279,1224,581,1242,700,1529,624,1584,1471,202,1211,1726,1255,1855,616,1834,1953,987,1441,798,1542,550,1715,1100,1047,1777,1929,543,735,1688,1683,345,1601,1420,1333,1229,958],[1502,1327,1647,1188,1430,1768,806,1875,565,1024,528,1258,603,490,935,438,301,1751,1161,1276,1606,1665,376,783,1143,1560,1571,663,697,1596,726,1128,313,1410,1020,1444,1935,1816,1346,912],[0.39,0.02,0.19,0.29,0.54,0.03,0.04,0.36,0.47,0.38,0.69,0.65,0.46,0.2,0.26,0.77,0.86,0.59,0.22,0.34,0.63,0.83,0.89,0.42,0.94,0.45,0.95,0.58,0.01,0.28,0.32,0.96,0.07,0.76,0.13,0.05,0.85,0.75,0.31,0.23],[-0.02,0.01,0.28,0.12,0.32,0,-0.5,-0.01,0.27,0.24,-0.11,-0.4,-0.06,0.31,0.15,0.41,0.42,-0.05,-0.16,-0.48,0.18,-0.45,0.05,0.02,0.43,0.04,-0.46,-0.25,-0.14,0.37,0.16,-0.34,-0.32,0.44,0.26,-0.43,-0.13,-0.42,-0.09,-0.2]],"container":"<table class=\"display\">\n  <thead>\n    <tr>\n      <th> <\/th>\n      <th>type1<\/th>\n      <th>type2<\/th>\n      <th>value<\/th>\n      <th>value1<\/th>\n      <th>value2<\/th>\n      <th>prob1<\/th>\n      <th>prob2<\/th>\n    <\/tr>\n  <\/thead>\n<\/table>","options":{"pageLength":5,"dom":"ftip","orderFixed":[[1,"asc"],[2,"desc"]],"columnDefs":[{"className":"dt-right","targets":[3,4,5,6,7]},{"orderable":false,"targets":0}],"order":[],"autoWidth":false,"orderClasses":false,"lengthMenu":[5,10,25,50,100]}},"evals":[],"jsHooks":[]}</script>

当指定排序方式的列较多时，也可以指定各列的排序优先级。通常在 `orderFixed = list()` 中写在前面的列排序优先级更高，但也可以用 pre/post 参数来设置。如下，pre 表示排序优先级更高， post 表示排序优先级更低。

``` r
datatable(data, options = list(orderFixed = list(
  pre = list(2, 'desc'),
  post = list(1, 'asc')
)))
```

<div id="htmlwidget-68" style="width:100%;height:auto;" class="datatables html-widget"></div>
<script type="application/json" data-for="htmlwidget-68">{"x":{"filter":"none","vertical":false,"data":[["1","2","3","4","5","6","7","8","9","10","11","12","13","14","15","16","17","18","19","20","21","22","23","24","25","26","27","28","29","30","31","32","33","34","35","36","37","38","39","40"],["A","A","B","B","C","C","D","D","E","E","F","F","G","G","H","H","I","I","J","J","K","K","L","L","M","M","N","N","O","O","P","P","Q","Q","R","R","S","S","T","T"],["NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES"],[2227,3458,4870,2707,2773,4750,2475,2122,4280,3293,3271,3521,2950,4159,4517,3988,2512,2799,4496,4425,4716,3547,3998,2827,2427,3989,2358,4197,2987,3130,2275,3597,3607,4499,2796,2193,4631,2492,4303,2233],[1134,1576,1510,1279,1224,581,1242,700,1529,624,1584,1471,202,1211,1726,1255,1855,616,1834,1953,987,1441,798,1542,550,1715,1100,1047,1777,1929,543,735,1688,1683,345,1601,1420,1333,1229,958],[1502,1327,1647,1188,1430,1768,806,1875,565,1024,528,1258,603,490,935,438,301,1751,1161,1276,1606,1665,376,783,1143,1560,1571,663,697,1596,726,1128,313,1410,1020,1444,1935,1816,1346,912],[0.39,0.02,0.19,0.29,0.54,0.03,0.04,0.36,0.47,0.38,0.69,0.65,0.46,0.2,0.26,0.77,0.86,0.59,0.22,0.34,0.63,0.83,0.89,0.42,0.94,0.45,0.95,0.58,0.01,0.28,0.32,0.96,0.07,0.76,0.13,0.05,0.85,0.75,0.31,0.23],[-0.02,0.01,0.28,0.12,0.32,0,-0.5,-0.01,0.27,0.24,-0.11,-0.4,-0.06,0.31,0.15,0.41,0.42,-0.05,-0.16,-0.48,0.18,-0.45,0.05,0.02,0.43,0.04,-0.46,-0.25,-0.14,0.37,0.16,-0.34,-0.32,0.44,0.26,-0.43,-0.13,-0.42,-0.09,-0.2]],"container":"<table class=\"display\">\n  <thead>\n    <tr>\n      <th> <\/th>\n      <th>type1<\/th>\n      <th>type2<\/th>\n      <th>value<\/th>\n      <th>value1<\/th>\n      <th>value2<\/th>\n      <th>prob1<\/th>\n      <th>prob2<\/th>\n    <\/tr>\n  <\/thead>\n<\/table>","options":{"pageLength":5,"dom":"ftip","orderFixed":{"pre":[2,"desc"],"post":[1,"asc"]},"columnDefs":[{"className":"dt-right","targets":[3,4,5,6,7]},{"orderable":false,"targets":0}],"order":[],"autoWidth":false,"orderClasses":false,"lengthMenu":[5,10,25,50,100]}},"evals":[],"jsHooks":[]}</script>

## 2.6.合并列·隐藏列（visible）

本小节介绍将表格中多列的单元格内容合并，并隐藏被合并的一列。如下对目标列引入 JS， `row[1]` 表示取此表格中第1列数据的值，`row[2]` 表示取此表格中第2列数据的值，将两列数据一起返回，合并后的数据便会展示在目标列的单元格中。

``` r
datatable(data, 
          options = list(
            columnDefs = list(
              list(
                targets = 1,
                render = JS("function(data, type, row, meta) {
                  return   row[1] + '-' + row[2]
                  }")
              ),
            list(targets = 2, visible = FALSE) # 隐藏第2列
)))
```

<div id="htmlwidget-69" style="width:100%;height:auto;" class="datatables html-widget"></div>
<script type="application/json" data-for="htmlwidget-69">{"x":{"filter":"none","vertical":false,"data":[["1","2","3","4","5","6","7","8","9","10","11","12","13","14","15","16","17","18","19","20","21","22","23","24","25","26","27","28","29","30","31","32","33","34","35","36","37","38","39","40"],["A","A","B","B","C","C","D","D","E","E","F","F","G","G","H","H","I","I","J","J","K","K","L","L","M","M","N","N","O","O","P","P","Q","Q","R","R","S","S","T","T"],["NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES"],[2227,3458,4870,2707,2773,4750,2475,2122,4280,3293,3271,3521,2950,4159,4517,3988,2512,2799,4496,4425,4716,3547,3998,2827,2427,3989,2358,4197,2987,3130,2275,3597,3607,4499,2796,2193,4631,2492,4303,2233],[1134,1576,1510,1279,1224,581,1242,700,1529,624,1584,1471,202,1211,1726,1255,1855,616,1834,1953,987,1441,798,1542,550,1715,1100,1047,1777,1929,543,735,1688,1683,345,1601,1420,1333,1229,958],[1502,1327,1647,1188,1430,1768,806,1875,565,1024,528,1258,603,490,935,438,301,1751,1161,1276,1606,1665,376,783,1143,1560,1571,663,697,1596,726,1128,313,1410,1020,1444,1935,1816,1346,912],[0.39,0.02,0.19,0.29,0.54,0.03,0.04,0.36,0.47,0.38,0.69,0.65,0.46,0.2,0.26,0.77,0.86,0.59,0.22,0.34,0.63,0.83,0.89,0.42,0.94,0.45,0.95,0.58,0.01,0.28,0.32,0.96,0.07,0.76,0.13,0.05,0.85,0.75,0.31,0.23],[-0.02,0.01,0.28,0.12,0.32,0,-0.5,-0.01,0.27,0.24,-0.11,-0.4,-0.06,0.31,0.15,0.41,0.42,-0.05,-0.16,-0.48,0.18,-0.45,0.05,0.02,0.43,0.04,-0.46,-0.25,-0.14,0.37,0.16,-0.34,-0.32,0.44,0.26,-0.43,-0.13,-0.42,-0.09,-0.2]],"container":"<table class=\"display\">\n  <thead>\n    <tr>\n      <th> <\/th>\n      <th>type1<\/th>\n      <th>type2<\/th>\n      <th>value<\/th>\n      <th>value1<\/th>\n      <th>value2<\/th>\n      <th>prob1<\/th>\n      <th>prob2<\/th>\n    <\/tr>\n  <\/thead>\n<\/table>","options":{"pageLength":5,"dom":"ftip","columnDefs":[{"targets":1,"render":"function(data, type, row, meta) {\n                  return   row[1] + '-' + row[2]\n                  }"},{"targets":2,"visible":false},{"className":"dt-right","targets":[3,4,5,6,7]},{"orderable":false,"targets":0}],"order":[],"autoWidth":false,"orderClasses":false,"lengthMenu":[5,10,25,50,100]}},"evals":["options.columnDefs.0.render"],"jsHooks":[]}</script>

## 2.7.编辑表格内容（editable）

编辑表格内容的参数是 editable ，可填入的参数值有 TRUE/FALSE、row、column、cell、all ，也可一个特别设定的列表。需要注意的是，不能编辑表头。

-   当 `editable = TRUE` 时，等同于 `editable = 'cell'`，即在展示的表格中双击选中某个单元格时，可以直接编辑该单元格中的内容。同理，若设定 `editable = 'row'`，表示可编辑一行数据，包含行名称。若设定 `editable = 'column'`，表示可编辑表格中的一列数据。若设定 `editable = 'all'`，可编辑整个表格主体。

-   当 `editable = FALSE` 时，不能编辑表格主体的内容。

-   需要对编辑功能做出更多详细设定时，须在 `editable= list()` 中写入更多参数。

    -   target：可填入 row、column、cell、all 中任一种。
    -   numeric：表示目标列仅能输入数字。
    -   area：表示目标列仅能输入文本，包含数字。
    -   disable：表示目标列不可编辑。

``` r
datatable(data, 
          editable = list(
            target = 'cell',
            numeric = c(1, 3), # 第1/3列仅能输入数字
            area = c(2, 4), # 第2/4列可输入任意文本，包含数字
            disable = list(columns = c(5, 6)) # 第5/6列不能编辑修改
          ))
```

<div id="htmlwidget-70" style="width:100%;height:auto;" class="datatables html-widget"></div>
<script type="application/json" data-for="htmlwidget-70">{"x":{"filter":"none","vertical":false,"editable":{"target":"cell","numeric":[1,3],"area":[2,4],"disable":{"columns":[5,6]}},"data":[["1","2","3","4","5","6","7","8","9","10","11","12","13","14","15","16","17","18","19","20","21","22","23","24","25","26","27","28","29","30","31","32","33","34","35","36","37","38","39","40"],["A","A","B","B","C","C","D","D","E","E","F","F","G","G","H","H","I","I","J","J","K","K","L","L","M","M","N","N","O","O","P","P","Q","Q","R","R","S","S","T","T"],["NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES"],[2227,3458,4870,2707,2773,4750,2475,2122,4280,3293,3271,3521,2950,4159,4517,3988,2512,2799,4496,4425,4716,3547,3998,2827,2427,3989,2358,4197,2987,3130,2275,3597,3607,4499,2796,2193,4631,2492,4303,2233],[1134,1576,1510,1279,1224,581,1242,700,1529,624,1584,1471,202,1211,1726,1255,1855,616,1834,1953,987,1441,798,1542,550,1715,1100,1047,1777,1929,543,735,1688,1683,345,1601,1420,1333,1229,958],[1502,1327,1647,1188,1430,1768,806,1875,565,1024,528,1258,603,490,935,438,301,1751,1161,1276,1606,1665,376,783,1143,1560,1571,663,697,1596,726,1128,313,1410,1020,1444,1935,1816,1346,912],[0.39,0.02,0.19,0.29,0.54,0.03,0.04,0.36,0.47,0.38,0.69,0.65,0.46,0.2,0.26,0.77,0.86,0.59,0.22,0.34,0.63,0.83,0.89,0.42,0.94,0.45,0.95,0.58,0.01,0.28,0.32,0.96,0.07,0.76,0.13,0.05,0.85,0.75,0.31,0.23],[-0.02,0.01,0.28,0.12,0.32,0,-0.5,-0.01,0.27,0.24,-0.11,-0.4,-0.06,0.31,0.15,0.41,0.42,-0.05,-0.16,-0.48,0.18,-0.45,0.05,0.02,0.43,0.04,-0.46,-0.25,-0.14,0.37,0.16,-0.34,-0.32,0.44,0.26,-0.43,-0.13,-0.42,-0.09,-0.2]],"container":"<table class=\"display\">\n  <thead>\n    <tr>\n      <th> <\/th>\n      <th>type1<\/th>\n      <th>type2<\/th>\n      <th>value<\/th>\n      <th>value1<\/th>\n      <th>value2<\/th>\n      <th>prob1<\/th>\n      <th>prob2<\/th>\n    <\/tr>\n  <\/thead>\n<\/table>","options":{"pageLength":5,"dom":"ftip","columnDefs":[{"className":"dt-right","targets":[3,4,5,6,7]},{"orderable":false,"targets":0}],"order":[],"autoWidth":false,"orderClasses":false,"lengthMenu":[5,10,25,50,100]}},"evals":[],"jsHooks":[]}</script>

## 2.8. 扩展功能（extensions）

DataTables 提供很多[扩展功能](https://datatables.net/extensions/index)，DT 官网中已对[这些扩展功能](https://rstudio.github.io/DT/extensions.html)作了简要介绍，它们的名称分别是 AutoFill、Buttons、ColReorder、FixedColumns、FixedHeader、KeyTable、Responsive、RowGroup、RowReorder、Scroller、SearchPanes、Select。本小节仅稍作补充。

### 2.8.1.冻结窗格（FixedColumns）

这里的冻结窗格功能和 EXCEL 的不大一样，只能冻结表格中最左边、最右边的列。

``` r
dt <- as.data.table(data)
dt.dcast <- data.table::dcast(dt, type2 ~ type1, value.var = "value")

datatable(
  dt.dcast,
  extensions = 'FixedColumns',
  options = list(
    dom = 't',
    scrollX = TRUE,
    fixedColumns = list(leftColumns = 2, rightColumns = 1)
  )
)
```

<div id="htmlwidget-71" style="width:100%;height:auto;" class="datatables html-widget"></div>
<script type="application/json" data-for="htmlwidget-71">{"x":{"filter":"none","vertical":false,"extensions":["FixedColumns"],"data":[["1","2"],["NO","YES"],[2227,3458],[4870,2707],[2773,4750],[2475,2122],[4280,3293],[3271,3521],[2950,4159],[4517,3988],[2512,2799],[4496,4425],[4716,3547],[3998,2827],[2427,3989],[2358,4197],[2987,3130],[2275,3597],[3607,4499],[2796,2193],[4631,2492],[4303,2233]],"container":"<table class=\"display\">\n  <thead>\n    <tr>\n      <th> <\/th>\n      <th>type2<\/th>\n      <th>A<\/th>\n      <th>B<\/th>\n      <th>C<\/th>\n      <th>D<\/th>\n      <th>E<\/th>\n      <th>F<\/th>\n      <th>G<\/th>\n      <th>H<\/th>\n      <th>I<\/th>\n      <th>J<\/th>\n      <th>K<\/th>\n      <th>L<\/th>\n      <th>M<\/th>\n      <th>N<\/th>\n      <th>O<\/th>\n      <th>P<\/th>\n      <th>Q<\/th>\n      <th>R<\/th>\n      <th>S<\/th>\n      <th>T<\/th>\n    <\/tr>\n  <\/thead>\n<\/table>","options":{"pageLength":5,"dom":"t","scrollX":true,"fixedColumns":{"leftColumns":2,"rightColumns":1},"columnDefs":[{"className":"dt-right","targets":[2,3,4,5,6,7,8,9,10,11,12,13,14,15,16,17,18,19,20,21]},{"orderable":false,"targets":0}],"order":[],"autoWidth":false,"orderClasses":false,"lengthMenu":[5,10,25,50,100]}},"evals":[],"jsHooks":[]}</script>

### 2.8.2.拖动列的位置（ColReorder）

-   定义列的默认位置。

``` r
datatable(data,
          extensions = 'ColReorder',
          options = list(colReorder = list(order = c(7, 6, 5, 4, 3, 2, 1, 0))))
```

<div id="htmlwidget-72" style="width:100%;height:auto;" class="datatables html-widget"></div>
<script type="application/json" data-for="htmlwidget-72">{"x":{"filter":"none","vertical":false,"extensions":["ColReorder"],"data":[["1","2","3","4","5","6","7","8","9","10","11","12","13","14","15","16","17","18","19","20","21","22","23","24","25","26","27","28","29","30","31","32","33","34","35","36","37","38","39","40"],["A","A","B","B","C","C","D","D","E","E","F","F","G","G","H","H","I","I","J","J","K","K","L","L","M","M","N","N","O","O","P","P","Q","Q","R","R","S","S","T","T"],["NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES"],[2227,3458,4870,2707,2773,4750,2475,2122,4280,3293,3271,3521,2950,4159,4517,3988,2512,2799,4496,4425,4716,3547,3998,2827,2427,3989,2358,4197,2987,3130,2275,3597,3607,4499,2796,2193,4631,2492,4303,2233],[1134,1576,1510,1279,1224,581,1242,700,1529,624,1584,1471,202,1211,1726,1255,1855,616,1834,1953,987,1441,798,1542,550,1715,1100,1047,1777,1929,543,735,1688,1683,345,1601,1420,1333,1229,958],[1502,1327,1647,1188,1430,1768,806,1875,565,1024,528,1258,603,490,935,438,301,1751,1161,1276,1606,1665,376,783,1143,1560,1571,663,697,1596,726,1128,313,1410,1020,1444,1935,1816,1346,912],[0.39,0.02,0.19,0.29,0.54,0.03,0.04,0.36,0.47,0.38,0.69,0.65,0.46,0.2,0.26,0.77,0.86,0.59,0.22,0.34,0.63,0.83,0.89,0.42,0.94,0.45,0.95,0.58,0.01,0.28,0.32,0.96,0.07,0.76,0.13,0.05,0.85,0.75,0.31,0.23],[-0.02,0.01,0.28,0.12,0.32,0,-0.5,-0.01,0.27,0.24,-0.11,-0.4,-0.06,0.31,0.15,0.41,0.42,-0.05,-0.16,-0.48,0.18,-0.45,0.05,0.02,0.43,0.04,-0.46,-0.25,-0.14,0.37,0.16,-0.34,-0.32,0.44,0.26,-0.43,-0.13,-0.42,-0.09,-0.2]],"container":"<table class=\"display\">\n  <thead>\n    <tr>\n      <th> <\/th>\n      <th>type1<\/th>\n      <th>type2<\/th>\n      <th>value<\/th>\n      <th>value1<\/th>\n      <th>value2<\/th>\n      <th>prob1<\/th>\n      <th>prob2<\/th>\n    <\/tr>\n  <\/thead>\n<\/table>","options":{"pageLength":5,"dom":"ftip","colReorder":{"order":[7,6,5,4,3,2,1,0]},"columnDefs":[{"className":"dt-right","targets":[3,4,5,6,7]},{"orderable":false,"targets":0}],"order":[],"autoWidth":false,"orderClasses":false,"lengthMenu":[5,10,25,50,100]}},"evals":[],"jsHooks":[]}</script>

-   手动[拖动列的位置](https://datatables.net/reference/option/colReorder)，对各列的位置进行重新排序。

``` r
datatable(data, extensions = 'ColReorder', options = list(colReorder = TRUE))
```

<div id="htmlwidget-73" style="width:100%;height:auto;" class="datatables html-widget"></div>
<script type="application/json" data-for="htmlwidget-73">{"x":{"filter":"none","vertical":false,"extensions":["ColReorder"],"data":[["1","2","3","4","5","6","7","8","9","10","11","12","13","14","15","16","17","18","19","20","21","22","23","24","25","26","27","28","29","30","31","32","33","34","35","36","37","38","39","40"],["A","A","B","B","C","C","D","D","E","E","F","F","G","G","H","H","I","I","J","J","K","K","L","L","M","M","N","N","O","O","P","P","Q","Q","R","R","S","S","T","T"],["NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES"],[2227,3458,4870,2707,2773,4750,2475,2122,4280,3293,3271,3521,2950,4159,4517,3988,2512,2799,4496,4425,4716,3547,3998,2827,2427,3989,2358,4197,2987,3130,2275,3597,3607,4499,2796,2193,4631,2492,4303,2233],[1134,1576,1510,1279,1224,581,1242,700,1529,624,1584,1471,202,1211,1726,1255,1855,616,1834,1953,987,1441,798,1542,550,1715,1100,1047,1777,1929,543,735,1688,1683,345,1601,1420,1333,1229,958],[1502,1327,1647,1188,1430,1768,806,1875,565,1024,528,1258,603,490,935,438,301,1751,1161,1276,1606,1665,376,783,1143,1560,1571,663,697,1596,726,1128,313,1410,1020,1444,1935,1816,1346,912],[0.39,0.02,0.19,0.29,0.54,0.03,0.04,0.36,0.47,0.38,0.69,0.65,0.46,0.2,0.26,0.77,0.86,0.59,0.22,0.34,0.63,0.83,0.89,0.42,0.94,0.45,0.95,0.58,0.01,0.28,0.32,0.96,0.07,0.76,0.13,0.05,0.85,0.75,0.31,0.23],[-0.02,0.01,0.28,0.12,0.32,0,-0.5,-0.01,0.27,0.24,-0.11,-0.4,-0.06,0.31,0.15,0.41,0.42,-0.05,-0.16,-0.48,0.18,-0.45,0.05,0.02,0.43,0.04,-0.46,-0.25,-0.14,0.37,0.16,-0.34,-0.32,0.44,0.26,-0.43,-0.13,-0.42,-0.09,-0.2]],"container":"<table class=\"display\">\n  <thead>\n    <tr>\n      <th> <\/th>\n      <th>type1<\/th>\n      <th>type2<\/th>\n      <th>value<\/th>\n      <th>value1<\/th>\n      <th>value2<\/th>\n      <th>prob1<\/th>\n      <th>prob2<\/th>\n    <\/tr>\n  <\/thead>\n<\/table>","options":{"pageLength":5,"dom":"ftip","colReorder":true,"columnDefs":[{"className":"dt-right","targets":[3,4,5,6,7]},{"orderable":false,"targets":0}],"order":[],"autoWidth":false,"orderClasses":false,"lengthMenu":[5,10,25,50,100]}},"evals":[],"jsHooks":[]}</script>

-   在固定窗格的条件下，拖动列的位置。

``` r
datatable(data,
          extensions = 'ColReorder',
          options = list(colReorder = list(
            fixedColumnsLeft = 2, # 固定最左边2列
            fixedColumnsRight = 1 # 固定最右边1列
          ))) 
```

<div id="htmlwidget-74" style="width:100%;height:auto;" class="datatables html-widget"></div>
<script type="application/json" data-for="htmlwidget-74">{"x":{"filter":"none","vertical":false,"extensions":["ColReorder"],"data":[["1","2","3","4","5","6","7","8","9","10","11","12","13","14","15","16","17","18","19","20","21","22","23","24","25","26","27","28","29","30","31","32","33","34","35","36","37","38","39","40"],["A","A","B","B","C","C","D","D","E","E","F","F","G","G","H","H","I","I","J","J","K","K","L","L","M","M","N","N","O","O","P","P","Q","Q","R","R","S","S","T","T"],["NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES"],[2227,3458,4870,2707,2773,4750,2475,2122,4280,3293,3271,3521,2950,4159,4517,3988,2512,2799,4496,4425,4716,3547,3998,2827,2427,3989,2358,4197,2987,3130,2275,3597,3607,4499,2796,2193,4631,2492,4303,2233],[1134,1576,1510,1279,1224,581,1242,700,1529,624,1584,1471,202,1211,1726,1255,1855,616,1834,1953,987,1441,798,1542,550,1715,1100,1047,1777,1929,543,735,1688,1683,345,1601,1420,1333,1229,958],[1502,1327,1647,1188,1430,1768,806,1875,565,1024,528,1258,603,490,935,438,301,1751,1161,1276,1606,1665,376,783,1143,1560,1571,663,697,1596,726,1128,313,1410,1020,1444,1935,1816,1346,912],[0.39,0.02,0.19,0.29,0.54,0.03,0.04,0.36,0.47,0.38,0.69,0.65,0.46,0.2,0.26,0.77,0.86,0.59,0.22,0.34,0.63,0.83,0.89,0.42,0.94,0.45,0.95,0.58,0.01,0.28,0.32,0.96,0.07,0.76,0.13,0.05,0.85,0.75,0.31,0.23],[-0.02,0.01,0.28,0.12,0.32,0,-0.5,-0.01,0.27,0.24,-0.11,-0.4,-0.06,0.31,0.15,0.41,0.42,-0.05,-0.16,-0.48,0.18,-0.45,0.05,0.02,0.43,0.04,-0.46,-0.25,-0.14,0.37,0.16,-0.34,-0.32,0.44,0.26,-0.43,-0.13,-0.42,-0.09,-0.2]],"container":"<table class=\"display\">\n  <thead>\n    <tr>\n      <th> <\/th>\n      <th>type1<\/th>\n      <th>type2<\/th>\n      <th>value<\/th>\n      <th>value1<\/th>\n      <th>value2<\/th>\n      <th>prob1<\/th>\n      <th>prob2<\/th>\n    <\/tr>\n  <\/thead>\n<\/table>","options":{"pageLength":5,"dom":"ftip","colReorder":{"fixedColumnsLeft":2,"fixedColumnsRight":1},"columnDefs":[{"className":"dt-right","targets":[3,4,5,6,7]},{"orderable":false,"targets":0}],"order":[],"autoWidth":false,"orderClasses":false,"lengthMenu":[5,10,25,50,100]}},"evals":[],"jsHooks":[]}</script>

### 2.8.3.拖动行的位置（RowReorder）

-   手动拖动行的位置，对各行的位置进行重新排序。默认情况下，单击一行中第一列的位置才能拖动行。

``` r
datatable(data,
          extensions = 'RowReorder',
          options = list(rowReorder = TRUE, order = list(c(0 , 'asc'))))
```

<div id="htmlwidget-75" style="width:100%;height:auto;" class="datatables html-widget"></div>
<script type="application/json" data-for="htmlwidget-75">{"x":{"filter":"none","vertical":false,"extensions":["RowReorder"],"data":[["1","2","3","4","5","6","7","8","9","10","11","12","13","14","15","16","17","18","19","20","21","22","23","24","25","26","27","28","29","30","31","32","33","34","35","36","37","38","39","40"],["A","A","B","B","C","C","D","D","E","E","F","F","G","G","H","H","I","I","J","J","K","K","L","L","M","M","N","N","O","O","P","P","Q","Q","R","R","S","S","T","T"],["NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES"],[2227,3458,4870,2707,2773,4750,2475,2122,4280,3293,3271,3521,2950,4159,4517,3988,2512,2799,4496,4425,4716,3547,3998,2827,2427,3989,2358,4197,2987,3130,2275,3597,3607,4499,2796,2193,4631,2492,4303,2233],[1134,1576,1510,1279,1224,581,1242,700,1529,624,1584,1471,202,1211,1726,1255,1855,616,1834,1953,987,1441,798,1542,550,1715,1100,1047,1777,1929,543,735,1688,1683,345,1601,1420,1333,1229,958],[1502,1327,1647,1188,1430,1768,806,1875,565,1024,528,1258,603,490,935,438,301,1751,1161,1276,1606,1665,376,783,1143,1560,1571,663,697,1596,726,1128,313,1410,1020,1444,1935,1816,1346,912],[0.39,0.02,0.19,0.29,0.54,0.03,0.04,0.36,0.47,0.38,0.69,0.65,0.46,0.2,0.26,0.77,0.86,0.59,0.22,0.34,0.63,0.83,0.89,0.42,0.94,0.45,0.95,0.58,0.01,0.28,0.32,0.96,0.07,0.76,0.13,0.05,0.85,0.75,0.31,0.23],[-0.02,0.01,0.28,0.12,0.32,0,-0.5,-0.01,0.27,0.24,-0.11,-0.4,-0.06,0.31,0.15,0.41,0.42,-0.05,-0.16,-0.48,0.18,-0.45,0.05,0.02,0.43,0.04,-0.46,-0.25,-0.14,0.37,0.16,-0.34,-0.32,0.44,0.26,-0.43,-0.13,-0.42,-0.09,-0.2]],"container":"<table class=\"display\">\n  <thead>\n    <tr>\n      <th> <\/th>\n      <th>type1<\/th>\n      <th>type2<\/th>\n      <th>value<\/th>\n      <th>value1<\/th>\n      <th>value2<\/th>\n      <th>prob1<\/th>\n      <th>prob2<\/th>\n    <\/tr>\n  <\/thead>\n<\/table>","options":{"pageLength":5,"dom":"ftip","rowReorder":true,"order":[["0","asc"]],"columnDefs":[{"className":"dt-right","targets":[3,4,5,6,7]},{"orderable":false,"targets":0}],"autoWidth":false,"orderClasses":false,"lengthMenu":[5,10,25,50,100]}},"evals":[],"jsHooks":[]}</script>

-   只有当鼠标单击一行的最后一列时，才能拖动行进行重新排序。若改成 `selector = 'td:first-child'`，改回默认参数值。若改成 `selector = 'tr'`，那么整行都可以拖动。

``` r
datatable(data,
          extensions = 'RowReorder',
          options = list(
            rowReorder = list(selector = 'td:last-child'),
            order = list(c(0 , 'asc'))
          ))
```

<div id="htmlwidget-76" style="width:100%;height:auto;" class="datatables html-widget"></div>
<script type="application/json" data-for="htmlwidget-76">{"x":{"filter":"none","vertical":false,"extensions":["RowReorder"],"data":[["1","2","3","4","5","6","7","8","9","10","11","12","13","14","15","16","17","18","19","20","21","22","23","24","25","26","27","28","29","30","31","32","33","34","35","36","37","38","39","40"],["A","A","B","B","C","C","D","D","E","E","F","F","G","G","H","H","I","I","J","J","K","K","L","L","M","M","N","N","O","O","P","P","Q","Q","R","R","S","S","T","T"],["NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES"],[2227,3458,4870,2707,2773,4750,2475,2122,4280,3293,3271,3521,2950,4159,4517,3988,2512,2799,4496,4425,4716,3547,3998,2827,2427,3989,2358,4197,2987,3130,2275,3597,3607,4499,2796,2193,4631,2492,4303,2233],[1134,1576,1510,1279,1224,581,1242,700,1529,624,1584,1471,202,1211,1726,1255,1855,616,1834,1953,987,1441,798,1542,550,1715,1100,1047,1777,1929,543,735,1688,1683,345,1601,1420,1333,1229,958],[1502,1327,1647,1188,1430,1768,806,1875,565,1024,528,1258,603,490,935,438,301,1751,1161,1276,1606,1665,376,783,1143,1560,1571,663,697,1596,726,1128,313,1410,1020,1444,1935,1816,1346,912],[0.39,0.02,0.19,0.29,0.54,0.03,0.04,0.36,0.47,0.38,0.69,0.65,0.46,0.2,0.26,0.77,0.86,0.59,0.22,0.34,0.63,0.83,0.89,0.42,0.94,0.45,0.95,0.58,0.01,0.28,0.32,0.96,0.07,0.76,0.13,0.05,0.85,0.75,0.31,0.23],[-0.02,0.01,0.28,0.12,0.32,0,-0.5,-0.01,0.27,0.24,-0.11,-0.4,-0.06,0.31,0.15,0.41,0.42,-0.05,-0.16,-0.48,0.18,-0.45,0.05,0.02,0.43,0.04,-0.46,-0.25,-0.14,0.37,0.16,-0.34,-0.32,0.44,0.26,-0.43,-0.13,-0.42,-0.09,-0.2]],"container":"<table class=\"display\">\n  <thead>\n    <tr>\n      <th> <\/th>\n      <th>type1<\/th>\n      <th>type2<\/th>\n      <th>value<\/th>\n      <th>value1<\/th>\n      <th>value2<\/th>\n      <th>prob1<\/th>\n      <th>prob2<\/th>\n    <\/tr>\n  <\/thead>\n<\/table>","options":{"pageLength":5,"dom":"ftip","rowReorder":{"selector":"td:last-child"},"order":[["0","asc"]],"columnDefs":[{"className":"dt-right","targets":[3,4,5,6,7]},{"orderable":false,"targets":0}],"autoWidth":false,"orderClasses":false,"lengthMenu":[5,10,25,50,100]}},"evals":[],"jsHooks":[]}</script>

### 2.8.4.行分组（rowGroup）

-   启用行分组。

``` r
datatable(
  data,
  rownames = FALSE,
  extensions = 'RowGroup',
  options = list(rowGroup = list(dataSrc = 0 # 指定用于行分组的列
                                 )))
```

<div id="htmlwidget-77" style="width:100%;height:auto;" class="datatables html-widget"></div>
<script type="application/json" data-for="htmlwidget-77">{"x":{"filter":"none","vertical":false,"extensions":["RowGroup"],"data":[["A","A","B","B","C","C","D","D","E","E","F","F","G","G","H","H","I","I","J","J","K","K","L","L","M","M","N","N","O","O","P","P","Q","Q","R","R","S","S","T","T"],["NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES"],[2227,3458,4870,2707,2773,4750,2475,2122,4280,3293,3271,3521,2950,4159,4517,3988,2512,2799,4496,4425,4716,3547,3998,2827,2427,3989,2358,4197,2987,3130,2275,3597,3607,4499,2796,2193,4631,2492,4303,2233],[1134,1576,1510,1279,1224,581,1242,700,1529,624,1584,1471,202,1211,1726,1255,1855,616,1834,1953,987,1441,798,1542,550,1715,1100,1047,1777,1929,543,735,1688,1683,345,1601,1420,1333,1229,958],[1502,1327,1647,1188,1430,1768,806,1875,565,1024,528,1258,603,490,935,438,301,1751,1161,1276,1606,1665,376,783,1143,1560,1571,663,697,1596,726,1128,313,1410,1020,1444,1935,1816,1346,912],[0.39,0.02,0.19,0.29,0.54,0.03,0.04,0.36,0.47,0.38,0.69,0.65,0.46,0.2,0.26,0.77,0.86,0.59,0.22,0.34,0.63,0.83,0.89,0.42,0.94,0.45,0.95,0.58,0.01,0.28,0.32,0.96,0.07,0.76,0.13,0.05,0.85,0.75,0.31,0.23],[-0.02,0.01,0.28,0.12,0.32,0,-0.5,-0.01,0.27,0.24,-0.11,-0.4,-0.06,0.31,0.15,0.41,0.42,-0.05,-0.16,-0.48,0.18,-0.45,0.05,0.02,0.43,0.04,-0.46,-0.25,-0.14,0.37,0.16,-0.34,-0.32,0.44,0.26,-0.43,-0.13,-0.42,-0.09,-0.2]],"container":"<table class=\"display\">\n  <thead>\n    <tr>\n      <th>type1<\/th>\n      <th>type2<\/th>\n      <th>value<\/th>\n      <th>value1<\/th>\n      <th>value2<\/th>\n      <th>prob1<\/th>\n      <th>prob2<\/th>\n    <\/tr>\n  <\/thead>\n<\/table>","options":{"pageLength":5,"dom":"ftip","rowGroup":{"dataSrc":0},"columnDefs":[{"className":"dt-right","targets":[2,3,4,5,6]}],"order":[],"autoWidth":false,"orderClasses":false,"lengthMenu":[5,10,25,50,100]}},"evals":[],"jsHooks":[]}</script>

-   起始行汇总。

此选项 [`rowGroup.startRender`](https://datatables.net/reference/option/rowGroup.startRender) 可以指定一个函数，该函数可以为分组的起始行返回一些复杂数据，如聚合、计数或其他摘要信息。每一次更改页面如分页、筛选或排序时，都会重新重新调用该函数，使得分组信息保持最新。

``` r
datatable(
  data,
  rownames = FALSE,
  extensions = 'RowGroup',
  options = list(
    rowGroup = list(
      dataSrc = 0,
      startClassName = 'table-start-group', # 默认值'table-group'
      startRender = JS(
        "function ( rows, group ) {
            return group +' (共'+rows.count()+'行)';
        }"
      ))))
```

<div id="htmlwidget-78" style="width:100%;height:auto;" class="datatables html-widget"></div>
<script type="application/json" data-for="htmlwidget-78">{"x":{"filter":"none","vertical":false,"extensions":["RowGroup"],"data":[["A","A","B","B","C","C","D","D","E","E","F","F","G","G","H","H","I","I","J","J","K","K","L","L","M","M","N","N","O","O","P","P","Q","Q","R","R","S","S","T","T"],["NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES"],[2227,3458,4870,2707,2773,4750,2475,2122,4280,3293,3271,3521,2950,4159,4517,3988,2512,2799,4496,4425,4716,3547,3998,2827,2427,3989,2358,4197,2987,3130,2275,3597,3607,4499,2796,2193,4631,2492,4303,2233],[1134,1576,1510,1279,1224,581,1242,700,1529,624,1584,1471,202,1211,1726,1255,1855,616,1834,1953,987,1441,798,1542,550,1715,1100,1047,1777,1929,543,735,1688,1683,345,1601,1420,1333,1229,958],[1502,1327,1647,1188,1430,1768,806,1875,565,1024,528,1258,603,490,935,438,301,1751,1161,1276,1606,1665,376,783,1143,1560,1571,663,697,1596,726,1128,313,1410,1020,1444,1935,1816,1346,912],[0.39,0.02,0.19,0.29,0.54,0.03,0.04,0.36,0.47,0.38,0.69,0.65,0.46,0.2,0.26,0.77,0.86,0.59,0.22,0.34,0.63,0.83,0.89,0.42,0.94,0.45,0.95,0.58,0.01,0.28,0.32,0.96,0.07,0.76,0.13,0.05,0.85,0.75,0.31,0.23],[-0.02,0.01,0.28,0.12,0.32,0,-0.5,-0.01,0.27,0.24,-0.11,-0.4,-0.06,0.31,0.15,0.41,0.42,-0.05,-0.16,-0.48,0.18,-0.45,0.05,0.02,0.43,0.04,-0.46,-0.25,-0.14,0.37,0.16,-0.34,-0.32,0.44,0.26,-0.43,-0.13,-0.42,-0.09,-0.2]],"container":"<table class=\"display\">\n  <thead>\n    <tr>\n      <th>type1<\/th>\n      <th>type2<\/th>\n      <th>value<\/th>\n      <th>value1<\/th>\n      <th>value2<\/th>\n      <th>prob1<\/th>\n      <th>prob2<\/th>\n    <\/tr>\n  <\/thead>\n<\/table>","options":{"pageLength":5,"dom":"ftip","rowGroup":{"dataSrc":0,"startClassName":"table-start-group","startRender":"function ( rows, group ) {\n            return group +' (共'+rows.count()+'行)';\n        }"},"columnDefs":[{"className":"dt-right","targets":[2,3,4,5,6]}],"order":[],"autoWidth":false,"orderClasses":false,"lengthMenu":[5,10,25,50,100]}},"evals":["options.rowGroup.startRender"],"jsHooks":[]}</script>

### 2.8.5.按键（buttons）

<!--editor:<https://editor.datatables.net/>-->

-   基本用法

``` r
datatable(data,
          extensions = 'Buttons',
          options = list(
            dom = 'Btip',
            buttons = list(
              'pageLength',
              list(
                extend = 'spacer',
                style = 'bar',
                text = '组别1'
              ),
              'copy',
              'copyHtml5',
              'print',
              list(
                extend = 'spacer',
                style = 'empty',
                text = '组别2'
              ),
              'csv',
              'csvHtml5',
              'excel',
              'excelHtml5',
              'pdf',
              'pdfHtml5'
            )
          ))
```

<div id="htmlwidget-79" style="width:100%;height:auto;" class="datatables html-widget"></div>
<script type="application/json" data-for="htmlwidget-79">{"x":{"filter":"none","vertical":false,"extensions":["Buttons"],"data":[["1","2","3","4","5","6","7","8","9","10","11","12","13","14","15","16","17","18","19","20","21","22","23","24","25","26","27","28","29","30","31","32","33","34","35","36","37","38","39","40"],["A","A","B","B","C","C","D","D","E","E","F","F","G","G","H","H","I","I","J","J","K","K","L","L","M","M","N","N","O","O","P","P","Q","Q","R","R","S","S","T","T"],["NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES"],[2227,3458,4870,2707,2773,4750,2475,2122,4280,3293,3271,3521,2950,4159,4517,3988,2512,2799,4496,4425,4716,3547,3998,2827,2427,3989,2358,4197,2987,3130,2275,3597,3607,4499,2796,2193,4631,2492,4303,2233],[1134,1576,1510,1279,1224,581,1242,700,1529,624,1584,1471,202,1211,1726,1255,1855,616,1834,1953,987,1441,798,1542,550,1715,1100,1047,1777,1929,543,735,1688,1683,345,1601,1420,1333,1229,958],[1502,1327,1647,1188,1430,1768,806,1875,565,1024,528,1258,603,490,935,438,301,1751,1161,1276,1606,1665,376,783,1143,1560,1571,663,697,1596,726,1128,313,1410,1020,1444,1935,1816,1346,912],[0.39,0.02,0.19,0.29,0.54,0.03,0.04,0.36,0.47,0.38,0.69,0.65,0.46,0.2,0.26,0.77,0.86,0.59,0.22,0.34,0.63,0.83,0.89,0.42,0.94,0.45,0.95,0.58,0.01,0.28,0.32,0.96,0.07,0.76,0.13,0.05,0.85,0.75,0.31,0.23],[-0.02,0.01,0.28,0.12,0.32,0,-0.5,-0.01,0.27,0.24,-0.11,-0.4,-0.06,0.31,0.15,0.41,0.42,-0.05,-0.16,-0.48,0.18,-0.45,0.05,0.02,0.43,0.04,-0.46,-0.25,-0.14,0.37,0.16,-0.34,-0.32,0.44,0.26,-0.43,-0.13,-0.42,-0.09,-0.2]],"container":"<table class=\"display\">\n  <thead>\n    <tr>\n      <th> <\/th>\n      <th>type1<\/th>\n      <th>type2<\/th>\n      <th>value<\/th>\n      <th>value1<\/th>\n      <th>value2<\/th>\n      <th>prob1<\/th>\n      <th>prob2<\/th>\n    <\/tr>\n  <\/thead>\n<\/table>","options":{"pageLength":5,"dom":"Btip","buttons":["pageLength",{"extend":"spacer","style":"bar","text":"组别1"},"copy","copyHtml5","print",{"extend":"spacer","style":"empty","text":"组别2"},"csv","csvHtml5","excel","excelHtml5","pdf","pdfHtml5"],"columnDefs":[{"className":"dt-right","targets":[3,4,5,6,7]},{"orderable":false,"targets":0}],"order":[],"autoWidth":false,"orderClasses":false,"lengthMenu":[5,10,25,50,100]}},"evals":[],"jsHooks":[]}</script>

-   扩展自定义（extend）

``` r
datatable(data,
          extensions = 'Buttons',
          options = list(dom = 'Btip',
                         buttons =
                           list(
                             list(
                               extend = 'copy',
                               text = '复制'
                             ),
                             list(
                               extend = 'print',
                               text = '打印'
                             ),
                             list(
                               extend = 'collection', # 集合按键
                               buttons = c('csv', 'excel', 'pdf'),
                               text = '下载'
                             )
                           )))
```

<div id="htmlwidget-80" style="width:100%;height:auto;" class="datatables html-widget"></div>
<script type="application/json" data-for="htmlwidget-80">{"x":{"filter":"none","vertical":false,"extensions":["Buttons"],"data":[["1","2","3","4","5","6","7","8","9","10","11","12","13","14","15","16","17","18","19","20","21","22","23","24","25","26","27","28","29","30","31","32","33","34","35","36","37","38","39","40"],["A","A","B","B","C","C","D","D","E","E","F","F","G","G","H","H","I","I","J","J","K","K","L","L","M","M","N","N","O","O","P","P","Q","Q","R","R","S","S","T","T"],["NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES"],[2227,3458,4870,2707,2773,4750,2475,2122,4280,3293,3271,3521,2950,4159,4517,3988,2512,2799,4496,4425,4716,3547,3998,2827,2427,3989,2358,4197,2987,3130,2275,3597,3607,4499,2796,2193,4631,2492,4303,2233],[1134,1576,1510,1279,1224,581,1242,700,1529,624,1584,1471,202,1211,1726,1255,1855,616,1834,1953,987,1441,798,1542,550,1715,1100,1047,1777,1929,543,735,1688,1683,345,1601,1420,1333,1229,958],[1502,1327,1647,1188,1430,1768,806,1875,565,1024,528,1258,603,490,935,438,301,1751,1161,1276,1606,1665,376,783,1143,1560,1571,663,697,1596,726,1128,313,1410,1020,1444,1935,1816,1346,912],[0.39,0.02,0.19,0.29,0.54,0.03,0.04,0.36,0.47,0.38,0.69,0.65,0.46,0.2,0.26,0.77,0.86,0.59,0.22,0.34,0.63,0.83,0.89,0.42,0.94,0.45,0.95,0.58,0.01,0.28,0.32,0.96,0.07,0.76,0.13,0.05,0.85,0.75,0.31,0.23],[-0.02,0.01,0.28,0.12,0.32,0,-0.5,-0.01,0.27,0.24,-0.11,-0.4,-0.06,0.31,0.15,0.41,0.42,-0.05,-0.16,-0.48,0.18,-0.45,0.05,0.02,0.43,0.04,-0.46,-0.25,-0.14,0.37,0.16,-0.34,-0.32,0.44,0.26,-0.43,-0.13,-0.42,-0.09,-0.2]],"container":"<table class=\"display\">\n  <thead>\n    <tr>\n      <th> <\/th>\n      <th>type1<\/th>\n      <th>type2<\/th>\n      <th>value<\/th>\n      <th>value1<\/th>\n      <th>value2<\/th>\n      <th>prob1<\/th>\n      <th>prob2<\/th>\n    <\/tr>\n  <\/thead>\n<\/table>","options":{"pageLength":5,"dom":"Btip","buttons":[{"extend":"copy","text":"复制"},{"extend":"print","text":"打印"},{"extend":"collection","buttons":["csv","excel","pdf"],"text":"下载"}],"columnDefs":[{"className":"dt-right","targets":[3,4,5,6,7]},{"orderable":false,"targets":0}],"order":[],"autoWidth":false,"orderClasses":false,"lengthMenu":[5,10,25,50,100]}},"evals":[],"jsHooks":[]}</script>

-   columnToggle

``` r
datatable(data,
          extensions = 'Buttons',
          options = list(dom = 'Btip',
                         buttons = list(
                           list(extend =  'columnToggle', columns = 1),
                           list(extend =  'columnToggle', columns = 2)
                         )))
```

<div id="htmlwidget-81" style="width:100%;height:auto;" class="datatables html-widget"></div>
<script type="application/json" data-for="htmlwidget-81">{"x":{"filter":"none","vertical":false,"extensions":["Buttons"],"data":[["1","2","3","4","5","6","7","8","9","10","11","12","13","14","15","16","17","18","19","20","21","22","23","24","25","26","27","28","29","30","31","32","33","34","35","36","37","38","39","40"],["A","A","B","B","C","C","D","D","E","E","F","F","G","G","H","H","I","I","J","J","K","K","L","L","M","M","N","N","O","O","P","P","Q","Q","R","R","S","S","T","T"],["NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES"],[2227,3458,4870,2707,2773,4750,2475,2122,4280,3293,3271,3521,2950,4159,4517,3988,2512,2799,4496,4425,4716,3547,3998,2827,2427,3989,2358,4197,2987,3130,2275,3597,3607,4499,2796,2193,4631,2492,4303,2233],[1134,1576,1510,1279,1224,581,1242,700,1529,624,1584,1471,202,1211,1726,1255,1855,616,1834,1953,987,1441,798,1542,550,1715,1100,1047,1777,1929,543,735,1688,1683,345,1601,1420,1333,1229,958],[1502,1327,1647,1188,1430,1768,806,1875,565,1024,528,1258,603,490,935,438,301,1751,1161,1276,1606,1665,376,783,1143,1560,1571,663,697,1596,726,1128,313,1410,1020,1444,1935,1816,1346,912],[0.39,0.02,0.19,0.29,0.54,0.03,0.04,0.36,0.47,0.38,0.69,0.65,0.46,0.2,0.26,0.77,0.86,0.59,0.22,0.34,0.63,0.83,0.89,0.42,0.94,0.45,0.95,0.58,0.01,0.28,0.32,0.96,0.07,0.76,0.13,0.05,0.85,0.75,0.31,0.23],[-0.02,0.01,0.28,0.12,0.32,0,-0.5,-0.01,0.27,0.24,-0.11,-0.4,-0.06,0.31,0.15,0.41,0.42,-0.05,-0.16,-0.48,0.18,-0.45,0.05,0.02,0.43,0.04,-0.46,-0.25,-0.14,0.37,0.16,-0.34,-0.32,0.44,0.26,-0.43,-0.13,-0.42,-0.09,-0.2]],"container":"<table class=\"display\">\n  <thead>\n    <tr>\n      <th> <\/th>\n      <th>type1<\/th>\n      <th>type2<\/th>\n      <th>value<\/th>\n      <th>value1<\/th>\n      <th>value2<\/th>\n      <th>prob1<\/th>\n      <th>prob2<\/th>\n    <\/tr>\n  <\/thead>\n<\/table>","options":{"pageLength":5,"dom":"Btip","buttons":[{"extend":"columnToggle","columns":1},{"extend":"columnToggle","columns":2}],"columnDefs":[{"className":"dt-right","targets":[3,4,5,6,7]},{"orderable":false,"targets":0}],"order":[],"autoWidth":false,"orderClasses":false,"lengthMenu":[5,10,25,50,100]}},"evals":[],"jsHooks":[]}</script>

-   columnsToggle

``` r
datatable(data,
          extensions = 'Buttons',
          options = list(dom = 'Btip',
                         buttons = list(
                           list(extend =  'columnsToggle')
                         )))
```

<div id="htmlwidget-82" style="width:100%;height:auto;" class="datatables html-widget"></div>
<script type="application/json" data-for="htmlwidget-82">{"x":{"filter":"none","vertical":false,"extensions":["Buttons"],"data":[["1","2","3","4","5","6","7","8","9","10","11","12","13","14","15","16","17","18","19","20","21","22","23","24","25","26","27","28","29","30","31","32","33","34","35","36","37","38","39","40"],["A","A","B","B","C","C","D","D","E","E","F","F","G","G","H","H","I","I","J","J","K","K","L","L","M","M","N","N","O","O","P","P","Q","Q","R","R","S","S","T","T"],["NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES"],[2227,3458,4870,2707,2773,4750,2475,2122,4280,3293,3271,3521,2950,4159,4517,3988,2512,2799,4496,4425,4716,3547,3998,2827,2427,3989,2358,4197,2987,3130,2275,3597,3607,4499,2796,2193,4631,2492,4303,2233],[1134,1576,1510,1279,1224,581,1242,700,1529,624,1584,1471,202,1211,1726,1255,1855,616,1834,1953,987,1441,798,1542,550,1715,1100,1047,1777,1929,543,735,1688,1683,345,1601,1420,1333,1229,958],[1502,1327,1647,1188,1430,1768,806,1875,565,1024,528,1258,603,490,935,438,301,1751,1161,1276,1606,1665,376,783,1143,1560,1571,663,697,1596,726,1128,313,1410,1020,1444,1935,1816,1346,912],[0.39,0.02,0.19,0.29,0.54,0.03,0.04,0.36,0.47,0.38,0.69,0.65,0.46,0.2,0.26,0.77,0.86,0.59,0.22,0.34,0.63,0.83,0.89,0.42,0.94,0.45,0.95,0.58,0.01,0.28,0.32,0.96,0.07,0.76,0.13,0.05,0.85,0.75,0.31,0.23],[-0.02,0.01,0.28,0.12,0.32,0,-0.5,-0.01,0.27,0.24,-0.11,-0.4,-0.06,0.31,0.15,0.41,0.42,-0.05,-0.16,-0.48,0.18,-0.45,0.05,0.02,0.43,0.04,-0.46,-0.25,-0.14,0.37,0.16,-0.34,-0.32,0.44,0.26,-0.43,-0.13,-0.42,-0.09,-0.2]],"container":"<table class=\"display\">\n  <thead>\n    <tr>\n      <th> <\/th>\n      <th>type1<\/th>\n      <th>type2<\/th>\n      <th>value<\/th>\n      <th>value1<\/th>\n      <th>value2<\/th>\n      <th>prob1<\/th>\n      <th>prob2<\/th>\n    <\/tr>\n  <\/thead>\n<\/table>","options":{"pageLength":5,"dom":"Btip","buttons":[{"extend":"columnsToggle"}],"columnDefs":[{"className":"dt-right","targets":[3,4,5,6,7]},{"orderable":false,"targets":0}],"order":[],"autoWidth":false,"orderClasses":false,"lengthMenu":[5,10,25,50,100]}},"evals":[],"jsHooks":[]}</script>

-   columnVisibility。如果不指定目标列，那么单击折叠按钮会把整个表折叠起来。

``` r
datatable(data,
          extensions = 'Buttons',
          options = list(dom = 'Btip',
                         buttons = list(
                           list(
                             extend = 'columnVisibility',
                             text = '展示',
                             visibility = TRUE,
                             columns=1
                           ),
                           list(
                             extend = 'columnVisibility',
                             text = '折叠',
                             visibility = FALSE,
                             columns=1
                           )
                         )))
```

<div id="htmlwidget-83" style="width:100%;height:auto;" class="datatables html-widget"></div>
<script type="application/json" data-for="htmlwidget-83">{"x":{"filter":"none","vertical":false,"extensions":["Buttons"],"data":[["1","2","3","4","5","6","7","8","9","10","11","12","13","14","15","16","17","18","19","20","21","22","23","24","25","26","27","28","29","30","31","32","33","34","35","36","37","38","39","40"],["A","A","B","B","C","C","D","D","E","E","F","F","G","G","H","H","I","I","J","J","K","K","L","L","M","M","N","N","O","O","P","P","Q","Q","R","R","S","S","T","T"],["NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES"],[2227,3458,4870,2707,2773,4750,2475,2122,4280,3293,3271,3521,2950,4159,4517,3988,2512,2799,4496,4425,4716,3547,3998,2827,2427,3989,2358,4197,2987,3130,2275,3597,3607,4499,2796,2193,4631,2492,4303,2233],[1134,1576,1510,1279,1224,581,1242,700,1529,624,1584,1471,202,1211,1726,1255,1855,616,1834,1953,987,1441,798,1542,550,1715,1100,1047,1777,1929,543,735,1688,1683,345,1601,1420,1333,1229,958],[1502,1327,1647,1188,1430,1768,806,1875,565,1024,528,1258,603,490,935,438,301,1751,1161,1276,1606,1665,376,783,1143,1560,1571,663,697,1596,726,1128,313,1410,1020,1444,1935,1816,1346,912],[0.39,0.02,0.19,0.29,0.54,0.03,0.04,0.36,0.47,0.38,0.69,0.65,0.46,0.2,0.26,0.77,0.86,0.59,0.22,0.34,0.63,0.83,0.89,0.42,0.94,0.45,0.95,0.58,0.01,0.28,0.32,0.96,0.07,0.76,0.13,0.05,0.85,0.75,0.31,0.23],[-0.02,0.01,0.28,0.12,0.32,0,-0.5,-0.01,0.27,0.24,-0.11,-0.4,-0.06,0.31,0.15,0.41,0.42,-0.05,-0.16,-0.48,0.18,-0.45,0.05,0.02,0.43,0.04,-0.46,-0.25,-0.14,0.37,0.16,-0.34,-0.32,0.44,0.26,-0.43,-0.13,-0.42,-0.09,-0.2]],"container":"<table class=\"display\">\n  <thead>\n    <tr>\n      <th> <\/th>\n      <th>type1<\/th>\n      <th>type2<\/th>\n      <th>value<\/th>\n      <th>value1<\/th>\n      <th>value2<\/th>\n      <th>prob1<\/th>\n      <th>prob2<\/th>\n    <\/tr>\n  <\/thead>\n<\/table>","options":{"pageLength":5,"dom":"Btip","buttons":[{"extend":"columnVisibility","text":"展示","visibility":true,"columns":1},{"extend":"columnVisibility","text":"折叠","visibility":false,"columns":1}],"columnDefs":[{"className":"dt-right","targets":[3,4,5,6,7]},{"orderable":false,"targets":0}],"order":[],"autoWidth":false,"orderClasses":false,"lengthMenu":[5,10,25,50,100]}},"evals":[],"jsHooks":[]}</script>

-   columnsVisibility。

``` r
datatable(data,
          extensions = 'Buttons',
          options = list(dom = 'Btip',
                         buttons = list(
                           list(
                             extend = 'columnsVisibility',
                             text = '展示',
                             visibility = TRUE
                           ),
                           list(
                             extend = 'columnsVisibility',
                             text = '折叠',
                             visibility = FALSE
                           )
                         )))
```

<div id="htmlwidget-84" style="width:100%;height:auto;" class="datatables html-widget"></div>
<script type="application/json" data-for="htmlwidget-84">{"x":{"filter":"none","vertical":false,"extensions":["Buttons"],"data":[["1","2","3","4","5","6","7","8","9","10","11","12","13","14","15","16","17","18","19","20","21","22","23","24","25","26","27","28","29","30","31","32","33","34","35","36","37","38","39","40"],["A","A","B","B","C","C","D","D","E","E","F","F","G","G","H","H","I","I","J","J","K","K","L","L","M","M","N","N","O","O","P","P","Q","Q","R","R","S","S","T","T"],["NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES"],[2227,3458,4870,2707,2773,4750,2475,2122,4280,3293,3271,3521,2950,4159,4517,3988,2512,2799,4496,4425,4716,3547,3998,2827,2427,3989,2358,4197,2987,3130,2275,3597,3607,4499,2796,2193,4631,2492,4303,2233],[1134,1576,1510,1279,1224,581,1242,700,1529,624,1584,1471,202,1211,1726,1255,1855,616,1834,1953,987,1441,798,1542,550,1715,1100,1047,1777,1929,543,735,1688,1683,345,1601,1420,1333,1229,958],[1502,1327,1647,1188,1430,1768,806,1875,565,1024,528,1258,603,490,935,438,301,1751,1161,1276,1606,1665,376,783,1143,1560,1571,663,697,1596,726,1128,313,1410,1020,1444,1935,1816,1346,912],[0.39,0.02,0.19,0.29,0.54,0.03,0.04,0.36,0.47,0.38,0.69,0.65,0.46,0.2,0.26,0.77,0.86,0.59,0.22,0.34,0.63,0.83,0.89,0.42,0.94,0.45,0.95,0.58,0.01,0.28,0.32,0.96,0.07,0.76,0.13,0.05,0.85,0.75,0.31,0.23],[-0.02,0.01,0.28,0.12,0.32,0,-0.5,-0.01,0.27,0.24,-0.11,-0.4,-0.06,0.31,0.15,0.41,0.42,-0.05,-0.16,-0.48,0.18,-0.45,0.05,0.02,0.43,0.04,-0.46,-0.25,-0.14,0.37,0.16,-0.34,-0.32,0.44,0.26,-0.43,-0.13,-0.42,-0.09,-0.2]],"container":"<table class=\"display\">\n  <thead>\n    <tr>\n      <th> <\/th>\n      <th>type1<\/th>\n      <th>type2<\/th>\n      <th>value<\/th>\n      <th>value1<\/th>\n      <th>value2<\/th>\n      <th>prob1<\/th>\n      <th>prob2<\/th>\n    <\/tr>\n  <\/thead>\n<\/table>","options":{"pageLength":5,"dom":"Btip","buttons":[{"extend":"columnsVisibility","text":"展示","visibility":true},{"extend":"columnsVisibility","text":"折叠","visibility":false}],"columnDefs":[{"className":"dt-right","targets":[3,4,5,6,7]},{"orderable":false,"targets":0}],"order":[],"autoWidth":false,"orderClasses":false,"lengthMenu":[5,10,25,50,100]}},"evals":[],"jsHooks":[]}</script>

-   colvis。

``` r
datatable(data,
          extensions = 'Buttons',
          options = list(dom = 'Btip',
                         buttons = 'colvis'))
```

<div id="htmlwidget-85" style="width:100%;height:auto;" class="datatables html-widget"></div>
<script type="application/json" data-for="htmlwidget-85">{"x":{"filter":"none","vertical":false,"extensions":["Buttons"],"data":[["1","2","3","4","5","6","7","8","9","10","11","12","13","14","15","16","17","18","19","20","21","22","23","24","25","26","27","28","29","30","31","32","33","34","35","36","37","38","39","40"],["A","A","B","B","C","C","D","D","E","E","F","F","G","G","H","H","I","I","J","J","K","K","L","L","M","M","N","N","O","O","P","P","Q","Q","R","R","S","S","T","T"],["NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES"],[2227,3458,4870,2707,2773,4750,2475,2122,4280,3293,3271,3521,2950,4159,4517,3988,2512,2799,4496,4425,4716,3547,3998,2827,2427,3989,2358,4197,2987,3130,2275,3597,3607,4499,2796,2193,4631,2492,4303,2233],[1134,1576,1510,1279,1224,581,1242,700,1529,624,1584,1471,202,1211,1726,1255,1855,616,1834,1953,987,1441,798,1542,550,1715,1100,1047,1777,1929,543,735,1688,1683,345,1601,1420,1333,1229,958],[1502,1327,1647,1188,1430,1768,806,1875,565,1024,528,1258,603,490,935,438,301,1751,1161,1276,1606,1665,376,783,1143,1560,1571,663,697,1596,726,1128,313,1410,1020,1444,1935,1816,1346,912],[0.39,0.02,0.19,0.29,0.54,0.03,0.04,0.36,0.47,0.38,0.69,0.65,0.46,0.2,0.26,0.77,0.86,0.59,0.22,0.34,0.63,0.83,0.89,0.42,0.94,0.45,0.95,0.58,0.01,0.28,0.32,0.96,0.07,0.76,0.13,0.05,0.85,0.75,0.31,0.23],[-0.02,0.01,0.28,0.12,0.32,0,-0.5,-0.01,0.27,0.24,-0.11,-0.4,-0.06,0.31,0.15,0.41,0.42,-0.05,-0.16,-0.48,0.18,-0.45,0.05,0.02,0.43,0.04,-0.46,-0.25,-0.14,0.37,0.16,-0.34,-0.32,0.44,0.26,-0.43,-0.13,-0.42,-0.09,-0.2]],"container":"<table class=\"display\">\n  <thead>\n    <tr>\n      <th> <\/th>\n      <th>type1<\/th>\n      <th>type2<\/th>\n      <th>value<\/th>\n      <th>value1<\/th>\n      <th>value2<\/th>\n      <th>prob1<\/th>\n      <th>prob2<\/th>\n    <\/tr>\n  <\/thead>\n<\/table>","options":{"pageLength":5,"dom":"Btip","buttons":["colvis"],"columnDefs":[{"className":"dt-right","targets":[3,4,5,6,7]},{"orderable":false,"targets":0}],"order":[],"autoWidth":false,"orderClasses":false,"lengthMenu":[5,10,25,50,100]}},"evals":[],"jsHooks":[]}</script>

# 第三章 应用场景

## 3.1.与其他包的交互

### 3.1.1.formattable 转换成 DT

静态表格包 [formattable](https://renkun-ken.github.io/formattable/) 中有一个函数`as.datatable()`可以将绘制出来的表格转换成 DT 表格。

``` r
library(formattable)

fmt <- formattable(
  data,
  list(
    type1 = formatter("span", style = x ~ ifelse(x == "A",
                                                 style(
                                                   color = "green", font.weight = "bold"
                                                 ), NA)), 
    type2 = formatter(
      "span",
      style = x ~ style(color = ifelse(x == 'YES', "green", "red")),
      x ~ icontext(ifelse(x == 'YES', "ok", "remove"), ifelse(x == 'YES', "Yes", "No"))
    ),
    value = color_tile("white", "orange"),
    area(col = c(value1, value2)) ~ normalize_bar("pink", 0.2),
    prob1 = formatter(
      "span",
      style = x ~ style(color = ifelse(rank(-x) <= 3, "green", "gray")),
      x ~ sprintf("%.2f (rank: %02d)", x, rank(-x))
    )
  )
)

as.datatable(fmt)
```

<div id="htmlwidget-86" style="width:100%;height:auto;" class="datatables html-widget"></div>
<script type="application/json" data-for="htmlwidget-86">{"x":{"filter":"none","vertical":false,"data":[["1","2","3","4","5","6","7","8","9","10","11","12","13","14","15","16","17","18","19","20","21","22","23","24","25","26","27","28","29","30","31","32","33","34","35","36","37","38","39","40"],["<span style=\"color: green; font-weight: bold\">A<\/span>","<span style=\"color: green; font-weight: bold\">A<\/span>","<span>B<\/span>                                        ","<span>B<\/span>                                        ","<span>C<\/span>                                        ","<span>C<\/span>                                        ","<span>D<\/span>                                        ","<span>D<\/span>                                        ","<span>E<\/span>                                        ","<span>E<\/span>                                        ","<span>F<\/span>                                        ","<span>F<\/span>                                        ","<span>G<\/span>                                        ","<span>G<\/span>                                        ","<span>H<\/span>                                        ","<span>H<\/span>                                        ","<span>I<\/span>                                        ","<span>I<\/span>                                        ","<span>J<\/span>                                        ","<span>J<\/span>                                        ","<span>K<\/span>                                        ","<span>K<\/span>                                        ","<span>L<\/span>                                        ","<span>L<\/span>                                        ","<span>M<\/span>                                        ","<span>M<\/span>                                        ","<span>N<\/span>                                        ","<span>N<\/span>                                        ","<span>O<\/span>                                        ","<span>O<\/span>                                        ","<span>P<\/span>                                        ","<span>P<\/span>                                        ","<span>Q<\/span>                                        ","<span>Q<\/span>                                        ","<span>R<\/span>                                        ","<span>R<\/span>                                        ","<span>S<\/span>                                        ","<span>S<\/span>                                        ","<span>T<\/span>                                        ","<span>T<\/span>                                        "],["<span style=\"color: red\">\n  <i class=\"glyphicon glyphicon-remove\"><\/i>\n  No\n<\/span>","<span style=\"color: green\">\n  <i class=\"glyphicon glyphicon-ok\"><\/i>\n  Yes\n<\/span> ","<span style=\"color: red\">\n  <i class=\"glyphicon glyphicon-remove\"><\/i>\n  No\n<\/span>","<span style=\"color: green\">\n  <i class=\"glyphicon glyphicon-ok\"><\/i>\n  Yes\n<\/span> ","<span style=\"color: red\">\n  <i class=\"glyphicon glyphicon-remove\"><\/i>\n  No\n<\/span>","<span style=\"color: green\">\n  <i class=\"glyphicon glyphicon-ok\"><\/i>\n  Yes\n<\/span> ","<span style=\"color: red\">\n  <i class=\"glyphicon glyphicon-remove\"><\/i>\n  No\n<\/span>","<span style=\"color: green\">\n  <i class=\"glyphicon glyphicon-ok\"><\/i>\n  Yes\n<\/span> ","<span style=\"color: red\">\n  <i class=\"glyphicon glyphicon-remove\"><\/i>\n  No\n<\/span>","<span style=\"color: green\">\n  <i class=\"glyphicon glyphicon-ok\"><\/i>\n  Yes\n<\/span> ","<span style=\"color: red\">\n  <i class=\"glyphicon glyphicon-remove\"><\/i>\n  No\n<\/span>","<span style=\"color: green\">\n  <i class=\"glyphicon glyphicon-ok\"><\/i>\n  Yes\n<\/span> ","<span style=\"color: red\">\n  <i class=\"glyphicon glyphicon-remove\"><\/i>\n  No\n<\/span>","<span style=\"color: green\">\n  <i class=\"glyphicon glyphicon-ok\"><\/i>\n  Yes\n<\/span> ","<span style=\"color: red\">\n  <i class=\"glyphicon glyphicon-remove\"><\/i>\n  No\n<\/span>","<span style=\"color: green\">\n  <i class=\"glyphicon glyphicon-ok\"><\/i>\n  Yes\n<\/span> ","<span style=\"color: red\">\n  <i class=\"glyphicon glyphicon-remove\"><\/i>\n  No\n<\/span>","<span style=\"color: green\">\n  <i class=\"glyphicon glyphicon-ok\"><\/i>\n  Yes\n<\/span> ","<span style=\"color: red\">\n  <i class=\"glyphicon glyphicon-remove\"><\/i>\n  No\n<\/span>","<span style=\"color: green\">\n  <i class=\"glyphicon glyphicon-ok\"><\/i>\n  Yes\n<\/span> ","<span style=\"color: red\">\n  <i class=\"glyphicon glyphicon-remove\"><\/i>\n  No\n<\/span>","<span style=\"color: green\">\n  <i class=\"glyphicon glyphicon-ok\"><\/i>\n  Yes\n<\/span> ","<span style=\"color: red\">\n  <i class=\"glyphicon glyphicon-remove\"><\/i>\n  No\n<\/span>","<span style=\"color: green\">\n  <i class=\"glyphicon glyphicon-ok\"><\/i>\n  Yes\n<\/span> ","<span style=\"color: red\">\n  <i class=\"glyphicon glyphicon-remove\"><\/i>\n  No\n<\/span>","<span style=\"color: green\">\n  <i class=\"glyphicon glyphicon-ok\"><\/i>\n  Yes\n<\/span> ","<span style=\"color: red\">\n  <i class=\"glyphicon glyphicon-remove\"><\/i>\n  No\n<\/span>","<span style=\"color: green\">\n  <i class=\"glyphicon glyphicon-ok\"><\/i>\n  Yes\n<\/span> ","<span style=\"color: red\">\n  <i class=\"glyphicon glyphicon-remove\"><\/i>\n  No\n<\/span>","<span style=\"color: green\">\n  <i class=\"glyphicon glyphicon-ok\"><\/i>\n  Yes\n<\/span> ","<span style=\"color: red\">\n  <i class=\"glyphicon glyphicon-remove\"><\/i>\n  No\n<\/span>","<span style=\"color: green\">\n  <i class=\"glyphicon glyphicon-ok\"><\/i>\n  Yes\n<\/span> ","<span style=\"color: red\">\n  <i class=\"glyphicon glyphicon-remove\"><\/i>\n  No\n<\/span>","<span style=\"color: green\">\n  <i class=\"glyphicon glyphicon-ok\"><\/i>\n  Yes\n<\/span> ","<span style=\"color: red\">\n  <i class=\"glyphicon glyphicon-remove\"><\/i>\n  No\n<\/span>","<span style=\"color: green\">\n  <i class=\"glyphicon glyphicon-ok\"><\/i>\n  Yes\n<\/span> ","<span style=\"color: red\">\n  <i class=\"glyphicon glyphicon-remove\"><\/i>\n  No\n<\/span>","<span style=\"color: green\">\n  <i class=\"glyphicon glyphicon-ok\"><\/i>\n  Yes\n<\/span> ","<span style=\"color: red\">\n  <i class=\"glyphicon glyphicon-remove\"><\/i>\n  No\n<\/span>","<span style=\"color: green\">\n  <i class=\"glyphicon glyphicon-ok\"><\/i>\n  Yes\n<\/span> "],["<span style=\"display: block; padding: 0 4px; border-radius: 4px; background-color: #fffbf5\">2227<\/span>","<span style=\"display: block; padding: 0 4px; border-radius: 4px; background-color: #ffd383\">3458<\/span>","<span style=\"display: block; padding: 0 4px; border-radius: 4px; background-color: #ffa500\">4870<\/span>","<span style=\"display: block; padding: 0 4px; border-radius: 4px; background-color: #ffebc8\">2707<\/span>","<span style=\"display: block; padding: 0 4px; border-radius: 4px; background-color: #ffe9c2\">2773<\/span>","<span style=\"display: block; padding: 0 4px; border-radius: 4px; background-color: #ffa80b\">4750<\/span>","<span style=\"display: block; padding: 0 4px; border-radius: 4px; background-color: #fff3de\">2475<\/span>","<span style=\"display: block; padding: 0 4px; border-radius: 4px; background-color: #ffffff\">2122<\/span>","<span style=\"display: block; padding: 0 4px; border-radius: 4px; background-color: #ffb836\">4280<\/span>","<span style=\"display: block; padding: 0 4px; border-radius: 4px; background-color: #ffd892\">3293<\/span>","<span style=\"display: block; padding: 0 4px; border-radius: 4px; background-color: #ffd994\">3271<\/span>","<span style=\"display: block; padding: 0 4px; border-radius: 4px; background-color: #ffd17d\">3521<\/span>","<span style=\"display: block; padding: 0 4px; border-radius: 4px; background-color: #ffe3b2\">2950<\/span>","<span style=\"display: block; padding: 0 4px; border-radius: 4px; background-color: #ffbc41\">4159<\/span>","<span style=\"display: block; padding: 0 4px; border-radius: 4px; background-color: #ffb020\">4517<\/span>","<span style=\"display: block; padding: 0 4px; border-radius: 4px; background-color: #ffc151\">3988<\/span>","<span style=\"display: block; padding: 0 4px; border-radius: 4px; background-color: #fff2da\">2512<\/span>","<span style=\"display: block; padding: 0 4px; border-radius: 4px; background-color: #ffe8c0\">2799<\/span>","<span style=\"display: block; padding: 0 4px; border-radius: 4px; background-color: #ffb122\">4496<\/span>","<span style=\"display: block; padding: 0 4px; border-radius: 4px; background-color: #ffb329\">4425<\/span>","<span style=\"display: block; padding: 0 4px; border-radius: 4px; background-color: #ffaa0e\">4716<\/span>","<span style=\"display: block; padding: 0 4px; border-radius: 4px; background-color: #ffd07a\">3547<\/span>","<span style=\"display: block; padding: 0 4px; border-radius: 4px; background-color: #ffc150\">3998<\/span>","<span style=\"display: block; padding: 0 4px; border-radius: 4px; background-color: #ffe7bd\">2827<\/span>","<span style=\"display: block; padding: 0 4px; border-radius: 4px; background-color: #fff5e2\">2427<\/span>","<span style=\"display: block; padding: 0 4px; border-radius: 4px; background-color: #ffc151\">3989<\/span>","<span style=\"display: block; padding: 0 4px; border-radius: 4px; background-color: #fff7e9\">2358<\/span>","<span style=\"display: block; padding: 0 4px; border-radius: 4px; background-color: #ffbb3e\">4197<\/span>","<span style=\"display: block; padding: 0 4px; border-radius: 4px; background-color: #ffe2ae\">2987<\/span>","<span style=\"display: block; padding: 0 4px; border-radius: 4px; background-color: #ffdda1\">3130<\/span>","<span style=\"display: block; padding: 0 4px; border-radius: 4px; background-color: #fff9f0\">2275<\/span>","<span style=\"display: block; padding: 0 4px; border-radius: 4px; background-color: #ffce76\">3597<\/span>","<span style=\"display: block; padding: 0 4px; border-radius: 4px; background-color: #ffce75\">3607<\/span>","<span style=\"display: block; padding: 0 4px; border-radius: 4px; background-color: #ffb122\">4499<\/span>","<span style=\"display: block; padding: 0 4px; border-radius: 4px; background-color: #ffe8c0\">2796<\/span>","<span style=\"display: block; padding: 0 4px; border-radius: 4px; background-color: #fffcf8\">2193<\/span>","<span style=\"display: block; padding: 0 4px; border-radius: 4px; background-color: #ffac16\">4631<\/span>","<span style=\"display: block; padding: 0 4px; border-radius: 4px; background-color: #fff2dc\">2492<\/span>","<span style=\"display: block; padding: 0 4px; border-radius: 4px; background-color: #ffb734\">4303<\/span>","<span style=\"display: block; padding: 0 4px; border-radius: 4px; background-color: #fffbf4\">2233<\/span>"],["<span style=\"display: inline-block; direction: rtl; unicode-bidi: plaintext; border-radius: 4px; padding-right: 2px; background-color: pink; width: 62.58%\">1134<\/span> ","<span style=\"display: inline-block; direction: rtl; unicode-bidi: plaintext; border-radius: 4px; padding-right: 2px; background-color: pink; width: 82.78%\">1576<\/span> ","<span style=\"display: inline-block; direction: rtl; unicode-bidi: plaintext; border-radius: 4px; padding-right: 2px; background-color: pink; width: 79.76%\">1510<\/span> ","<span style=\"display: inline-block; direction: rtl; unicode-bidi: plaintext; border-radius: 4px; padding-right: 2px; background-color: pink; width: 69.21%\">1279<\/span> ","<span style=\"display: inline-block; direction: rtl; unicode-bidi: plaintext; border-radius: 4px; padding-right: 2px; background-color: pink; width: 66.69%\">1224<\/span> ","<span style=\"display: inline-block; direction: rtl; unicode-bidi: plaintext; border-radius: 4px; padding-right: 2px; background-color: pink; width: 37.32%\">581<\/span>  ","<span style=\"display: inline-block; direction: rtl; unicode-bidi: plaintext; border-radius: 4px; padding-right: 2px; background-color: pink; width: 67.52%\">1242<\/span> ","<span style=\"display: inline-block; direction: rtl; unicode-bidi: plaintext; border-radius: 4px; padding-right: 2px; background-color: pink; width: 42.75%\">700<\/span>  ","<span style=\"display: inline-block; direction: rtl; unicode-bidi: plaintext; border-radius: 4px; padding-right: 2px; background-color: pink; width: 80.63%\">1529<\/span> ","<span style=\"display: inline-block; direction: rtl; unicode-bidi: plaintext; border-radius: 4px; padding-right: 2px; background-color: pink; width: 39.28%\">624<\/span>  ","<span style=\"display: inline-block; direction: rtl; unicode-bidi: plaintext; border-radius: 4px; padding-right: 2px; background-color: pink; width: 83.14%\">1584<\/span> ","<span style=\"display: inline-block; direction: rtl; unicode-bidi: plaintext; border-radius: 4px; padding-right: 2px; background-color: pink; width: 77.98%\">1471<\/span> ","<span style=\"display: inline-block; direction: rtl; unicode-bidi: plaintext; border-radius: 4px; padding-right: 2px; background-color: pink; width: 20.00%\">202<\/span>  ","<span style=\"display: inline-block; direction: rtl; unicode-bidi: plaintext; border-radius: 4px; padding-right: 2px; background-color: pink; width: 66.10%\">1211<\/span> ","<span style=\"display: inline-block; direction: rtl; unicode-bidi: plaintext; border-radius: 4px; padding-right: 2px; background-color: pink; width: 89.63%\">1726<\/span> ","<span style=\"display: inline-block; direction: rtl; unicode-bidi: plaintext; border-radius: 4px; padding-right: 2px; background-color: pink; width: 68.11%\">1255<\/span> ","<span style=\"display: inline-block; direction: rtl; unicode-bidi: plaintext; border-radius: 4px; padding-right: 2px; background-color: pink; width: 95.52%\">1855<\/span> ","<span style=\"display: inline-block; direction: rtl; unicode-bidi: plaintext; border-radius: 4px; padding-right: 2px; background-color: pink; width: 38.91%\">616<\/span>  ","<span style=\"display: inline-block; direction: rtl; unicode-bidi: plaintext; border-radius: 4px; padding-right: 2px; background-color: pink; width: 94.56%\">1834<\/span> ","<span style=\"display: inline-block; direction: rtl; unicode-bidi: plaintext; border-radius: 4px; padding-right: 2px; background-color: pink; width: 100.00%\">1953<\/span>","<span style=\"display: inline-block; direction: rtl; unicode-bidi: plaintext; border-radius: 4px; padding-right: 2px; background-color: pink; width: 55.87%\">987<\/span>  ","<span style=\"display: inline-block; direction: rtl; unicode-bidi: plaintext; border-radius: 4px; padding-right: 2px; background-color: pink; width: 76.61%\">1441<\/span> ","<span style=\"display: inline-block; direction: rtl; unicode-bidi: plaintext; border-radius: 4px; padding-right: 2px; background-color: pink; width: 47.23%\">798<\/span>  ","<span style=\"display: inline-block; direction: rtl; unicode-bidi: plaintext; border-radius: 4px; padding-right: 2px; background-color: pink; width: 81.22%\">1542<\/span> ","<span style=\"display: inline-block; direction: rtl; unicode-bidi: plaintext; border-radius: 4px; padding-right: 2px; background-color: pink; width: 35.90%\">550<\/span>  ","<span style=\"display: inline-block; direction: rtl; unicode-bidi: plaintext; border-radius: 4px; padding-right: 2px; background-color: pink; width: 89.13%\">1715<\/span> ","<span style=\"display: inline-block; direction: rtl; unicode-bidi: plaintext; border-radius: 4px; padding-right: 2px; background-color: pink; width: 61.03%\">1100<\/span> ","<span style=\"display: inline-block; direction: rtl; unicode-bidi: plaintext; border-radius: 4px; padding-right: 2px; background-color: pink; width: 58.61%\">1047<\/span> ","<span style=\"display: inline-block; direction: rtl; unicode-bidi: plaintext; border-radius: 4px; padding-right: 2px; background-color: pink; width: 91.96%\">1777<\/span> ","<span style=\"display: inline-block; direction: rtl; unicode-bidi: plaintext; border-radius: 4px; padding-right: 2px; background-color: pink; width: 98.90%\">1929<\/span> ","<span style=\"display: inline-block; direction: rtl; unicode-bidi: plaintext; border-radius: 4px; padding-right: 2px; background-color: pink; width: 35.58%\">543<\/span>  ","<span style=\"display: inline-block; direction: rtl; unicode-bidi: plaintext; border-radius: 4px; padding-right: 2px; background-color: pink; width: 44.35%\">735<\/span>  ","<span style=\"display: inline-block; direction: rtl; unicode-bidi: plaintext; border-radius: 4px; padding-right: 2px; background-color: pink; width: 87.89%\">1688<\/span> ","<span style=\"display: inline-block; direction: rtl; unicode-bidi: plaintext; border-radius: 4px; padding-right: 2px; background-color: pink; width: 87.66%\">1683<\/span> ","<span style=\"display: inline-block; direction: rtl; unicode-bidi: plaintext; border-radius: 4px; padding-right: 2px; background-color: pink; width: 26.53%\">345<\/span>  ","<span style=\"display: inline-block; direction: rtl; unicode-bidi: plaintext; border-radius: 4px; padding-right: 2px; background-color: pink; width: 83.92%\">1601<\/span> ","<span style=\"display: inline-block; direction: rtl; unicode-bidi: plaintext; border-radius: 4px; padding-right: 2px; background-color: pink; width: 75.65%\">1420<\/span> ","<span style=\"display: inline-block; direction: rtl; unicode-bidi: plaintext; border-radius: 4px; padding-right: 2px; background-color: pink; width: 71.67%\">1333<\/span> ","<span style=\"display: inline-block; direction: rtl; unicode-bidi: plaintext; border-radius: 4px; padding-right: 2px; background-color: pink; width: 66.92%\">1229<\/span> ","<span style=\"display: inline-block; direction: rtl; unicode-bidi: plaintext; border-radius: 4px; padding-right: 2px; background-color: pink; width: 54.54%\">958<\/span>  "],["<span style=\"display: inline-block; direction: rtl; unicode-bidi: plaintext; border-radius: 4px; padding-right: 2px; background-color: pink; width: 79.39%\">1502<\/span> ","<span style=\"display: inline-block; direction: rtl; unicode-bidi: plaintext; border-radius: 4px; padding-right: 2px; background-color: pink; width: 71.40%\">1327<\/span> ","<span style=\"display: inline-block; direction: rtl; unicode-bidi: plaintext; border-radius: 4px; padding-right: 2px; background-color: pink; width: 86.02%\">1647<\/span> ","<span style=\"display: inline-block; direction: rtl; unicode-bidi: plaintext; border-radius: 4px; padding-right: 2px; background-color: pink; width: 65.05%\">1188<\/span> ","<span style=\"display: inline-block; direction: rtl; unicode-bidi: plaintext; border-radius: 4px; padding-right: 2px; background-color: pink; width: 76.11%\">1430<\/span> ","<span style=\"display: inline-block; direction: rtl; unicode-bidi: plaintext; border-radius: 4px; padding-right: 2px; background-color: pink; width: 91.55%\">1768<\/span> ","<span style=\"display: inline-block; direction: rtl; unicode-bidi: plaintext; border-radius: 4px; padding-right: 2px; background-color: pink; width: 47.60%\">806<\/span>  ","<span style=\"display: inline-block; direction: rtl; unicode-bidi: plaintext; border-radius: 4px; padding-right: 2px; background-color: pink; width: 96.44%\">1875<\/span> ","<span style=\"display: inline-block; direction: rtl; unicode-bidi: plaintext; border-radius: 4px; padding-right: 2px; background-color: pink; width: 36.58%\">565<\/span>  ","<span style=\"display: inline-block; direction: rtl; unicode-bidi: plaintext; border-radius: 4px; padding-right: 2px; background-color: pink; width: 57.56%\">1024<\/span> ","<span style=\"display: inline-block; direction: rtl; unicode-bidi: plaintext; border-radius: 4px; padding-right: 2px; background-color: pink; width: 34.89%\">528<\/span>  ","<span style=\"display: inline-block; direction: rtl; unicode-bidi: plaintext; border-radius: 4px; padding-right: 2px; background-color: pink; width: 68.25%\">1258<\/span> ","<span style=\"display: inline-block; direction: rtl; unicode-bidi: plaintext; border-radius: 4px; padding-right: 2px; background-color: pink; width: 38.32%\">603<\/span>  ","<span style=\"display: inline-block; direction: rtl; unicode-bidi: plaintext; border-radius: 4px; padding-right: 2px; background-color: pink; width: 33.16%\">490<\/span>  ","<span style=\"display: inline-block; direction: rtl; unicode-bidi: plaintext; border-radius: 4px; padding-right: 2px; background-color: pink; width: 53.49%\">935<\/span>  ","<span style=\"display: inline-block; direction: rtl; unicode-bidi: plaintext; border-radius: 4px; padding-right: 2px; background-color: pink; width: 30.78%\">438<\/span>  ","<span style=\"display: inline-block; direction: rtl; unicode-bidi: plaintext; border-radius: 4px; padding-right: 2px; background-color: pink; width: 24.52%\">301<\/span>  ","<span style=\"display: inline-block; direction: rtl; unicode-bidi: plaintext; border-radius: 4px; padding-right: 2px; background-color: pink; width: 90.77%\">1751<\/span> ","<span style=\"display: inline-block; direction: rtl; unicode-bidi: plaintext; border-radius: 4px; padding-right: 2px; background-color: pink; width: 63.81%\">1161<\/span> ","<span style=\"display: inline-block; direction: rtl; unicode-bidi: plaintext; border-radius: 4px; padding-right: 2px; background-color: pink; width: 69.07%\">1276<\/span> ","<span style=\"display: inline-block; direction: rtl; unicode-bidi: plaintext; border-radius: 4px; padding-right: 2px; background-color: pink; width: 84.15%\">1606<\/span> ","<span style=\"display: inline-block; direction: rtl; unicode-bidi: plaintext; border-radius: 4px; padding-right: 2px; background-color: pink; width: 86.84%\">1665<\/span> ","<span style=\"display: inline-block; direction: rtl; unicode-bidi: plaintext; border-radius: 4px; padding-right: 2px; background-color: pink; width: 27.95%\">376<\/span>  ","<span style=\"display: inline-block; direction: rtl; unicode-bidi: plaintext; border-radius: 4px; padding-right: 2px; background-color: pink; width: 46.54%\">783<\/span>  ","<span style=\"display: inline-block; direction: rtl; unicode-bidi: plaintext; border-radius: 4px; padding-right: 2px; background-color: pink; width: 62.99%\">1143<\/span> ","<span style=\"display: inline-block; direction: rtl; unicode-bidi: plaintext; border-radius: 4px; padding-right: 2px; background-color: pink; width: 82.04%\">1560<\/span> ","<span style=\"display: inline-block; direction: rtl; unicode-bidi: plaintext; border-radius: 4px; padding-right: 2px; background-color: pink; width: 82.55%\">1571<\/span> ","<span style=\"display: inline-block; direction: rtl; unicode-bidi: plaintext; border-radius: 4px; padding-right: 2px; background-color: pink; width: 41.06%\">663<\/span>  ","<span style=\"display: inline-block; direction: rtl; unicode-bidi: plaintext; border-radius: 4px; padding-right: 2px; background-color: pink; width: 42.62%\">697<\/span>  ","<span style=\"display: inline-block; direction: rtl; unicode-bidi: plaintext; border-radius: 4px; padding-right: 2px; background-color: pink; width: 83.69%\">1596<\/span> ","<span style=\"display: inline-block; direction: rtl; unicode-bidi: plaintext; border-radius: 4px; padding-right: 2px; background-color: pink; width: 43.94%\">726<\/span>  ","<span style=\"display: inline-block; direction: rtl; unicode-bidi: plaintext; border-radius: 4px; padding-right: 2px; background-color: pink; width: 62.31%\">1128<\/span> ","<span style=\"display: inline-block; direction: rtl; unicode-bidi: plaintext; border-radius: 4px; padding-right: 2px; background-color: pink; width: 25.07%\">313<\/span>  ","<span style=\"display: inline-block; direction: rtl; unicode-bidi: plaintext; border-radius: 4px; padding-right: 2px; background-color: pink; width: 75.19%\">1410<\/span> ","<span style=\"display: inline-block; direction: rtl; unicode-bidi: plaintext; border-radius: 4px; padding-right: 2px; background-color: pink; width: 57.37%\">1020<\/span> ","<span style=\"display: inline-block; direction: rtl; unicode-bidi: plaintext; border-radius: 4px; padding-right: 2px; background-color: pink; width: 76.74%\">1444<\/span> ","<span style=\"display: inline-block; direction: rtl; unicode-bidi: plaintext; border-radius: 4px; padding-right: 2px; background-color: pink; width: 99.18%\">1935<\/span> ","<span style=\"display: inline-block; direction: rtl; unicode-bidi: plaintext; border-radius: 4px; padding-right: 2px; background-color: pink; width: 93.74%\">1816<\/span> ","<span style=\"display: inline-block; direction: rtl; unicode-bidi: plaintext; border-radius: 4px; padding-right: 2px; background-color: pink; width: 72.27%\">1346<\/span> ","<span style=\"display: inline-block; direction: rtl; unicode-bidi: plaintext; border-radius: 4px; padding-right: 2px; background-color: pink; width: 52.44%\">912<\/span>  "],["<span style=\"color: gray\">0.39 (rank: 21)<\/span> ","<span style=\"color: gray\">0.02 (rank: 39)<\/span> ","<span style=\"color: gray\">0.19 (rank: 33)<\/span> ","<span style=\"color: gray\">0.29 (rank: 27)<\/span> ","<span style=\"color: gray\">0.54 (rank: 16)<\/span> ","<span style=\"color: gray\">0.03 (rank: 38)<\/span> ","<span style=\"color: gray\">0.04 (rank: 37)<\/span> ","<span style=\"color: gray\">0.36 (rank: 23)<\/span> ","<span style=\"color: gray\">0.47 (rank: 17)<\/span> ","<span style=\"color: gray\">0.38 (rank: 22)<\/span> ","<span style=\"color: gray\">0.69 (rank: 11)<\/span> ","<span style=\"color: gray\">0.65 (rank: 12)<\/span> ","<span style=\"color: gray\">0.46 (rank: 18)<\/span> ","<span style=\"color: gray\">0.20 (rank: 32)<\/span> ","<span style=\"color: gray\">0.26 (rank: 29)<\/span> ","<span style=\"color: gray\">0.77 (rank: 08)<\/span> ","<span style=\"color: gray\">0.86 (rank: 05)<\/span> ","<span style=\"color: gray\">0.59 (rank: 14)<\/span> ","<span style=\"color: gray\">0.22 (rank: 31)<\/span> ","<span style=\"color: gray\">0.34 (rank: 24)<\/span> ","<span style=\"color: gray\">0.63 (rank: 13)<\/span> ","<span style=\"color: gray\">0.83 (rank: 07)<\/span> ","<span style=\"color: gray\">0.89 (rank: 04)<\/span> ","<span style=\"color: gray\">0.42 (rank: 20)<\/span> ","<span style=\"color: green\">0.94 (rank: 03)<\/span>","<span style=\"color: gray\">0.45 (rank: 19)<\/span> ","<span style=\"color: green\">0.95 (rank: 02)<\/span>","<span style=\"color: gray\">0.58 (rank: 15)<\/span> ","<span style=\"color: gray\">0.01 (rank: 40)<\/span> ","<span style=\"color: gray\">0.28 (rank: 28)<\/span> ","<span style=\"color: gray\">0.32 (rank: 25)<\/span> ","<span style=\"color: green\">0.96 (rank: 01)<\/span>","<span style=\"color: gray\">0.07 (rank: 35)<\/span> ","<span style=\"color: gray\">0.76 (rank: 09)<\/span> ","<span style=\"color: gray\">0.13 (rank: 34)<\/span> ","<span style=\"color: gray\">0.05 (rank: 36)<\/span> ","<span style=\"color: gray\">0.85 (rank: 06)<\/span> ","<span style=\"color: gray\">0.75 (rank: 10)<\/span> ","<span style=\"color: gray\">0.31 (rank: 26)<\/span> ","<span style=\"color: gray\">0.23 (rank: 30)<\/span> "],["-0.02","0.01","0.28","0.12","0.32","0.00","-0.50","-0.01","0.27","0.24","-0.11","-0.40","-0.06","0.31","0.15","0.41","0.42","-0.05","-0.16","-0.48","0.18","-0.45","0.05","0.02","0.43","0.04","-0.46","-0.25","-0.14","0.37","0.16","-0.34","-0.32","0.44","0.26","-0.43","-0.13","-0.42","-0.09","-0.20"]],"container":"<table class=\"display\">\n  <thead>\n    <tr>\n      <th> <\/th>\n      <th>type1<\/th>\n      <th>type2<\/th>\n      <th>value<\/th>\n      <th>value1<\/th>\n      <th>value2<\/th>\n      <th>prob1<\/th>\n      <th>prob2<\/th>\n    <\/tr>\n  <\/thead>\n<\/table>","options":{"pageLength":5,"dom":"ftip","columnDefs":[{"orderable":false,"targets":0}],"order":[],"autoWidth":false,"orderClasses":false,"lengthMenu":[5,10,25,50,100]}},"evals":[],"jsHooks":[]}</script>

### 3.1.2.使用 crosstalk 实现图表数据共享

当支持 crosstalk 的交互式绘图包和交互式表格包一起使用时，可以通过 crosstalk 实现图表数据共享，比如 plotly 和 DT。

``` r
library(crosstalk)

shared_data <- SharedData$new(data)

bscols(list(
  plotly::plot_ly(
    data = shared_data,
    type = 'scatter',
    mode = 'markers+text',
    x =  ~ value1,
    y =  ~ value2,
    color =  ~ type2
  ),
  DT::datatable(
    shared_data,
    width = '100%',
    rownames = FALSE,
    filter = 'bottom',
    # 允许使用正则，[A|B]表示多选A或B
    options = list(search = list(regex = TRUE))
  )
))
```

<div class="container-fluid crosstalk-bscols">
<div class="row">
<div class="col-xs-12">
<div id="htmlwidget-87" style="width:100%;height:400px;" class="plotly html-widget"></div>
<script type="application/json" data-for="htmlwidget-87">{"x":{"visdat":{"400423c44f03":["function () ","plotlyVisDat"]},"cur_data":"400423c44f03","attrs":{"400423c44f03":{"mode":"markers+text","x":{},"y":{},"color":{},"alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"scatter"}},"layout":{"margin":{"b":40,"l":60,"t":25,"r":10},"xaxis":{"domain":[0,1],"automargin":true,"title":"value1"},"yaxis":{"domain":[0,1],"automargin":true,"title":"value2"},"dragmode":"zoom","hovermode":"closest","showlegend":true},"source":"A","config":{"modeBarButtonsToAdd":["hoverclosest","hovercompare"],"showSendToCloud":false},"data":[{"mode":"markers+text","x":[1134,1510,1224,1242,1529,1584,202,1726,1855,1834,987,798,550,1100,1777,543,1688,345,1420,1229],"y":[1502,1647,1430,806,565,528,603,935,301,1161,1606,376,1143,1571,697,726,313,1020,1935,1346],"type":"scatter","key":["1","3","5","7","9","11","13","15","17","19","21","23","25","27","29","31","33","35","37","39"],"set":"SharedDatadcce205e","name":"NO","marker":{"color":"rgba(102,194,165,1)","line":{"color":"rgba(102,194,165,1)"}},"textfont":{"color":"rgba(102,194,165,1)"},"error_y":{"color":"rgba(102,194,165,1)"},"error_x":{"color":"rgba(102,194,165,1)"},"line":{"color":"rgba(102,194,165,1)"},"xaxis":"x","yaxis":"y","_isNestedKey":false,"frame":null},{"mode":"markers+text","x":[1576,1279,581,700,624,1471,1211,1255,616,1953,1441,1542,1715,1047,1929,735,1683,1601,1333,958],"y":[1327,1188,1768,1875,1024,1258,490,438,1751,1276,1665,783,1560,663,1596,1128,1410,1444,1816,912],"type":"scatter","key":["2","4","6","8","10","12","14","16","18","20","22","24","26","28","30","32","34","36","38","40"],"set":"SharedDatadcce205e","name":"YES","marker":{"color":"rgba(141,160,203,1)","line":{"color":"rgba(141,160,203,1)"}},"textfont":{"color":"rgba(141,160,203,1)"},"error_y":{"color":"rgba(141,160,203,1)"},"error_x":{"color":"rgba(141,160,203,1)"},"line":{"color":"rgba(141,160,203,1)"},"xaxis":"x","yaxis":"y","_isNestedKey":false,"frame":null}],"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0,"ctGroups":["SharedDatadcce205e"]},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>
<div id="htmlwidget-88" style="width:100%;height:auto;" class="datatables html-widget"></div>
<script type="application/json" data-for="htmlwidget-88">{"x":{"crosstalkOptions":{"key":["1","2","3","4","5","6","7","8","9","10","11","12","13","14","15","16","17","18","19","20","21","22","23","24","25","26","27","28","29","30","31","32","33","34","35","36","37","38","39","40"],"group":"SharedDatadcce205e"},"filter":"bottom","vertical":false,"filterHTML":"<tr>\n  <td data-type=\"character\" style=\"vertical-align: top;\">\n    <div class=\"form-group has-feedback\" style=\"margin-bottom: auto;\">\n      <input type=\"search\" placeholder=\"All\" class=\"form-control\" style=\"width: 100%;\"/>\n      <span class=\"glyphicon glyphicon-remove-circle form-control-feedback\"><\/span>\n    <\/div>\n  <\/td>\n  <td data-type=\"character\" style=\"vertical-align: top;\">\n    <div class=\"form-group has-feedback\" style=\"margin-bottom: auto;\">\n      <input type=\"search\" placeholder=\"All\" class=\"form-control\" style=\"width: 100%;\"/>\n      <span class=\"glyphicon glyphicon-remove-circle form-control-feedback\"><\/span>\n    <\/div>\n  <\/td>\n  <td data-type=\"integer\" style=\"vertical-align: top;\">\n    <div class=\"form-group has-feedback\" style=\"margin-bottom: auto;\">\n      <input type=\"search\" placeholder=\"All\" class=\"form-control\" style=\"width: 100%;\"/>\n      <span class=\"glyphicon glyphicon-remove-circle form-control-feedback\"><\/span>\n    <\/div>\n    <div style=\"display: none;position: absolute;width: 200px;opacity: 1\">\n      <div data-min=\"2122\" data-max=\"4870\"><\/div>\n      <span style=\"float: left;\"><\/span>\n      <span style=\"float: right;\"><\/span>\n    <\/div>\n  <\/td>\n  <td data-type=\"integer\" style=\"vertical-align: top;\">\n    <div class=\"form-group has-feedback\" style=\"margin-bottom: auto;\">\n      <input type=\"search\" placeholder=\"All\" class=\"form-control\" style=\"width: 100%;\"/>\n      <span class=\"glyphicon glyphicon-remove-circle form-control-feedback\"><\/span>\n    <\/div>\n    <div style=\"display: none;position: absolute;width: 200px;opacity: 1\">\n      <div data-min=\"202\" data-max=\"1953\"><\/div>\n      <span style=\"float: left;\"><\/span>\n      <span style=\"float: right;\"><\/span>\n    <\/div>\n  <\/td>\n  <td data-type=\"integer\" style=\"vertical-align: top;\">\n    <div class=\"form-group has-feedback\" style=\"margin-bottom: auto;\">\n      <input type=\"search\" placeholder=\"All\" class=\"form-control\" style=\"width: 100%;\"/>\n      <span class=\"glyphicon glyphicon-remove-circle form-control-feedback\"><\/span>\n    <\/div>\n    <div style=\"display: none;position: absolute;width: 200px;opacity: 1\">\n      <div data-min=\"301\" data-max=\"1935\"><\/div>\n      <span style=\"float: left;\"><\/span>\n      <span style=\"float: right;\"><\/span>\n    <\/div>\n  <\/td>\n  <td data-type=\"number\" style=\"vertical-align: top;\">\n    <div class=\"form-group has-feedback\" style=\"margin-bottom: auto;\">\n      <input type=\"search\" placeholder=\"All\" class=\"form-control\" style=\"width: 100%;\"/>\n      <span class=\"glyphicon glyphicon-remove-circle form-control-feedback\"><\/span>\n    <\/div>\n    <div style=\"display: none;position: absolute;width: 200px;opacity: 1\">\n      <div data-min=\"0.01\" data-max=\"0.96\" data-scale=\"2\"><\/div>\n      <span style=\"float: left;\"><\/span>\n      <span style=\"float: right;\"><\/span>\n    <\/div>\n  <\/td>\n  <td data-type=\"number\" style=\"vertical-align: top;\">\n    <div class=\"form-group has-feedback\" style=\"margin-bottom: auto;\">\n      <input type=\"search\" placeholder=\"All\" class=\"form-control\" style=\"width: 100%;\"/>\n      <span class=\"glyphicon glyphicon-remove-circle form-control-feedback\"><\/span>\n    <\/div>\n    <div style=\"display: none;position: absolute;width: 200px;opacity: 1\">\n      <div data-min=\"-0.5\" data-max=\"0.44\" data-scale=\"2\"><\/div>\n      <span style=\"float: left;\"><\/span>\n      <span style=\"float: right;\"><\/span>\n    <\/div>\n  <\/td>\n<\/tr>","data":[["A","A","B","B","C","C","D","D","E","E","F","F","G","G","H","H","I","I","J","J","K","K","L","L","M","M","N","N","O","O","P","P","Q","Q","R","R","S","S","T","T"],["NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES","NO","YES"],[2227,3458,4870,2707,2773,4750,2475,2122,4280,3293,3271,3521,2950,4159,4517,3988,2512,2799,4496,4425,4716,3547,3998,2827,2427,3989,2358,4197,2987,3130,2275,3597,3607,4499,2796,2193,4631,2492,4303,2233],[1134,1576,1510,1279,1224,581,1242,700,1529,624,1584,1471,202,1211,1726,1255,1855,616,1834,1953,987,1441,798,1542,550,1715,1100,1047,1777,1929,543,735,1688,1683,345,1601,1420,1333,1229,958],[1502,1327,1647,1188,1430,1768,806,1875,565,1024,528,1258,603,490,935,438,301,1751,1161,1276,1606,1665,376,783,1143,1560,1571,663,697,1596,726,1128,313,1410,1020,1444,1935,1816,1346,912],[0.39,0.02,0.19,0.29,0.54,0.03,0.04,0.36,0.47,0.38,0.69,0.65,0.46,0.2,0.26,0.77,0.86,0.59,0.22,0.34,0.63,0.83,0.89,0.42,0.94,0.45,0.95,0.58,0.01,0.28,0.32,0.96,0.07,0.76,0.13,0.05,0.85,0.75,0.31,0.23],[-0.02,0.01,0.28,0.12,0.32,0,-0.5,-0.01,0.27,0.24,-0.11,-0.4,-0.06,0.31,0.15,0.41,0.42,-0.05,-0.16,-0.48,0.18,-0.45,0.05,0.02,0.43,0.04,-0.46,-0.25,-0.14,0.37,0.16,-0.34,-0.32,0.44,0.26,-0.43,-0.13,-0.42,-0.09,-0.2]],"container":"<table class=\"display\">\n  <thead>\n    <tr>\n      <th>type1<\/th>\n      <th>type2<\/th>\n      <th>value<\/th>\n      <th>value1<\/th>\n      <th>value2<\/th>\n      <th>prob1<\/th>\n      <th>prob2<\/th>\n    <\/tr>\n  <\/thead>\n<\/table>","options":{"pageLength":5,"dom":"ftip","search":{"regex":true},"columnDefs":[{"className":"dt-right","targets":[2,3,4,5,6]}],"order":[],"autoWidth":false,"orderClasses":false,"lengthMenu":[5,10,25,50,100]},"selection":{"mode":"multiple","selected":null,"target":"row","selectable":null}},"evals":[],"jsHooks":[]}</script>
</div>
</div>
</div>

## 3.2.一些疑惑

在信息交流媒介仍为纸质的时代，在任何空白区域随意画上几横几竖便可画出表格的雏形，作为对信息进行组织整理、分门别类的工具，表格的基本功能仅仅是用线条将所记录的数据细节一项项隔离开。而到了电子化时代，随着所需记录或展示的信息变多（横向增加或纵向增加），简单的线条虽然勉强满足需求，但人们显然希望表格展示的内容能够更加一目了然。如果表格横向增加的列数变多，那么可以设置更多的静态样式如边框线、背景颜色等提升可视化的区分度。如果表格纵向增加的行数变多，那么可以设置更多的动态效果如分页、排序、筛选等提高交互使用的便捷性。

笔者将应用表格的目的分作三个基本场景：数据展示、数据探索、数据操作。与此相关的，表格的用处或优势大概可以总结为：数据展示、交流，分门别类、组织整理数据，更多数据细节，更多交互操作功能等。在此基础上，笔者想捋捋几个倍感疑惑的问题。

1.使用 R 包绘制表格时用 R 和引入 css/html/js 的边界

当人们开始记录大量数据并且试图展示出来的时候，一定是先绘制出了表格，随后才发明出各种可视化图形。也正是因为图形更能浓缩展示信息，在电子化时代各种绘图系统发展得更快更完善，也更加独立。在 R 的绘图系统中，比如 ggplot2， 就是用纯纯的 R 语言绘图；又如 plotly，它有 R 版本、Python 版本、js 版本，不同语言版本也都是在各自范围内形成独立的绘图系统；又如源自 echarts 的 echarts4r，也是尽可能把各类图形元素封装到独立的 R 函数中去实现，但又由于跟原生库之间的关系，留了一些可以引入 js 的接口。即便是在修改基础样式、图形主题等方面，这些图形库也是尽可能将可修改的内容圈定在一个范围内，免去用户要学习css/js 的麻烦。它们都以牺牲一定的自由来换取了独立。

可是表格绘制系统的发展似乎整体上是滞后的，也是不那么独立的，而且还分成了两种发展方向，即偏向于数据展示的静态表格包，和偏向于数据探索的交互表格包。一些静态展示表格包如 KableExtra、formattable、gt 等更寻求独立，因此所能实现的功能便框定在已有函数的范围之内。另一些动态交互表格包如 reactable、DT 等更寻求自由（PS也可能是因为开发者苟延残喘），因此留有引入 js/css 的接口。比如要在表格中“插入图片”，用 DT 包实现的话，就是用回调函数引入纯纯的 js 或者直接在数据中引入 css/html 来实现；用 reactable 包实现的话也是相似的，但也可以借用 htmltools包 把 html 中的 div、image 元素挪到 R 中用作div、image函数。

对于 R 中的表格包来说，独立和自由似乎是两个不可兼顾、只可取舍的方向[^2]。若要自由，那么就像 reactable、DT 一样，必须能引入 css/html/js，因为这两个包本身就源于不同的 js 库，而使用者也免不了需要了解 R 以外的其他语言，不能只写纯纯的 R。若要独立，那么就像 KableExtra、formattable、gt、reactablefmtr 一样，把许多功能封装到 R 函数里，用 R 重写一遍，各类功能以数量较大的函数或函数里的参数出现。

对工具的使用者来说，要是有一个表格包被开发得尽善尽美，只用写纯纯的 R 就能实现一切功能是再好不过。不然的话，要么多学几个各有特色的独立表格包，要么学一点简单的 css/js 基础。

2.做数据展示/探索时，使用表格和图形的边界

图形的优势在于图形种类丰富，信息浓缩后，数据的价值一目了然。而表格的优势大概有以下几点。

-   绘制图形时是需要有参照坐标系的，而绘制表格时不需要，当数据维度较多时，表格能展示出更多的数据细节。

-   表格里能够容纳的数据格式更加丰富，比如可以插入图片、图标、迷你图等。

-   表格的功能性更强，与数据的交互更加直接，比如交互式表格里的数据可以编辑、新增、删除。

在展示/探索数据时，图形和表格这两种工具应是相辅相成的，而不是必须二择其一的。

[^1]: 笔者是南方人，普通话讲得不好，“表格包”三个字说快了容易嘴瓢说成“表格标”。于是乎，加上一个“子”字，变成“表格包子”，说起来的时候，断句自然变成“表格”和“包子”，这样笔者就不会讲错了。

[^2]: 这里不絮叨 R 江湖里宗派众多，各大宗小派语法都不统一的问题。
