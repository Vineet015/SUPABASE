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
          SUPABASE_URL: ${{ secrets.SUPABASE_URL }}
          SUPABASE_KEY: ${{ secrets.SUPABASE_SERVICE_KEY }}
        run: |
          curl -X POST "https://hxihijefgrzcadwgamjt.supabase.co/rest/v1/ping" \   
            -H "apikey: eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJzdXBhYmFzZSIsInJlZiI6Imh4aWhpamVmZ3J6Y2Fkd2dhbWp0Iiwicm9sZSI6InNlcnZpY2Vfcm9sZSIsImlhdCI6MTc3NzQ4Mzk2NywiZXhwIjoyMDkzMDU5OTY3fQ.cdxA6HFAGv9gm4H5Fb7phQzlJP208cmBLBvtllGLlv0 \                
            -H "Authorization: Bearer $SUPABASE_KEY" \
            -H "Content-Type: application/json" \
            -d '{}'
