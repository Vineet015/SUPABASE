name: Keep Supabase Alive

on:
  schedule:
    - cron: '0 9 * * 1,4'   
  workflow_dispatch:         

jobs:
  ping:
    runs-on: ubuntu-latest
    steps:
      - name: Insert ping row
        env:
          SUPABASE_URL: ${{"https://hxihijefgrzcadwgamjt.supabase.co"}}
          SUPABASE_KEY: ${{ secrets.SUPABASE_SERVICE_KEY }}
        run: |
          curl -X POST "$https://hxihijefgrzcadwgamjt.supabase.co/rest/v1/ping" \
            -H "apikey: $SUPABASE_KEY" \
            -H "Authorization: Bearer $SUPABASE_KEY" \
            -H "Content-Type: application/json" \
            -d '{}'
