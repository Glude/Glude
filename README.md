# Visit https://github.com/lowlighter/metrics#-documentation for full reference
name: Metrics
on:
  # Schedule updates (each hour)
  schedule: [{cron: "0 * * * *"}]
  # Lines below let you run workflow manually and on each commit
  workflow_dispatch:
  push: {branches: ["master", "main"]}
jobs:
  github-metrics:
    runs-on: ubuntu-latest
    permissions:
      contents: write
    steps:
      - uses: lowlighter/metrics@latest
        with:
          # Your GitHub token
          # The following scopes are required:
          #  - public_access (default scope)
          # The following additional scopes may be required:
          #  - read:org      (for organization related metrics)
          #  - read:user     (for user related data)
          #  - read:packages (for some packages related data)
          #  - repo          (optional, if you want to include private repositories)
          token: ${{ secrets.METRICS_TOKEN }}

          # Options
          user: Glude
          template: terminal
          base: header, activity, community, repositories, metadata
          config_timezone: Europe/Berlin
          plugin_discussions: yes
          plugin_discussions_categories: yes
          plugin_fortune: yes
          plugin_introduction: yes
          plugin_introduction_title: yes
          plugin_isocalendar: yes
          plugin_isocalendar_duration: full-year
          plugin_languages: yes
          plugin_languages_analysis_timeout: 15
          plugin_languages_analysis_timeout_repositories: 7.5
          plugin_languages_categories: markup, programming
          plugin_languages_colors: github
          plugin_languages_ignored: html,css,react,javascript,java,reverse-engeenering
          plugin_languages_limit: 8
          plugin_languages_recent_categories: markup, programming
          plugin_languages_recent_days: 14
          plugin_languages_recent_load: 300
          plugin_languages_sections: most-used
          plugin_languages_threshold: 0%
          plugin_music: yes
          plugin_music_limit: 4
          plugin_music_mode: playlist
          plugin_music_playlist: https://open.spotify.com/playlist/5YKm5Zt0AUdKrlrvWzUV6l?si=f91972e015374523
          plugin_music_provider: spotify
          plugin_music_time_range: short
          plugin_music_top_type: tracks
          plugin_music_user: .user.login
          plugin_poopmap: yes
          plugin_poopmap_days: 7
          plugin_topics: yes
          plugin_topics_limit: 15
          plugin_topics_mode: icons
          plugin_topics_sort: random
