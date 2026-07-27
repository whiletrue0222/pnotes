source "https://rubygems.org"

gem "jekyll", "~> 4.4"
gem "jekyll-theme-hacker", "~> 0.2"

group :jekyll_plugins do
  gem "jekyll-feed", "~> 0.17"
  gem "jekyll-sitemap", "~> 1.4"
  gem "jekyll-redirect-from", "~> 0.16"
  # 테마 레이아웃이 site.github.* 를 참조한다 (푸터, CSS 캐시 버스팅).
  gem "jekyll-github-metadata", "~> 2.16"
end

# _config.yml 이 kramdown.input: GFM 을 쓰므로 별도 파서 gem 이 필요하다.
gem "kramdown-parser-gfm", "~> 1.1"

# Ruby 3.0 부터 webrick 이 표준 라이브러리에서 빠져서 `jekyll serve` 에 필요하다.
gem "webrick", "~> 1.9"

# jekyll-github-metadata 가 쓰는 octokit/faraday 의 retry 미들웨어 경고를 없앤다.
gem "faraday-retry", "~> 2.3"
