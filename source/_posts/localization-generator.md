---
title: "Ruby On Rails\_- Localization Generator"
id: 240
comment: false
categories:
  - 頭殼壞去
date: 2006-08-15 06:55:00
tags:
---

修改 app/controllers/application.rb:

   require 'localization'
    class ApplicationController &lt;&gt;        include Localization

修改 app/helpers/application_helper.rb:

  module ApplicationHelper
      include Localization

在 config/environment.rb 最後加上:

  require 'environments/localization_environment'
    require 'localization'
    Localization::load_localized_strings

修改 localization_environment.rb:

  :default_language = 'zhtw'

建立 lang/zhtw.yaml:

  file_charset: big5

這樣就能正常使用 Localization Generator 了，
否則會遭遇到 Iconv 的轉換問題。