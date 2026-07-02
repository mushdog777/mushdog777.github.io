source "https://rubygems.org"

# Jekyll 버전 유지 (현재 버전인 4.4.1 호환)
gem "jekyll", "~> 4.4.1"

# [변경] 기존 minima 테마를 주석 처리(또는 삭제)하고 Hydejack 테마를 추가합니다.
# gem "minima", "~> 2.5"
gem "jekyll-theme-hydejack", "~> 9.1"

# [변경] Hydejack이 정상 작동하기 위해 필요한 필수 플러그인 그룹입니다.
group :jekyll_plugins do
  gem "jekyll-feed", "~> 0.12"
  gem "jekyll-sitemap"
  gem "jekyll-gist"
  gem "jekyll-paginate"
end

# Windows 환경 및 기타 호환성을 위한 기존 설정 유지
platforms :mingw, :x64_mingw, :mswin, :jruby do
  gem "tzinfo", ">= 1", "< 3"
  gem "tzinfo-data"
end

gem "wdm", "~> 0.1", :platforms => [:mingw, :x64_mingw, :mswin]
gem "http_parser.rb", "~> 0.6.0", :platforms => [:jruby]
