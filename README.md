# export-kobo

Please read [pettarin/export-kobo](https://github.com/pettarin/export-kobo) for basic usage.

## Usages

- Confidential info: Prepare your `.env` file on the same directory

    ```bash
    # SENDER_EMAIL=your@gmail.com
    # APP_PASSWORD=your_app_specific_password
    # RECEIVER_EMAIL=recipient@example.com
    # NOTION_TOKEN=secret_xxxx
    # NOTION_DATABASE_ID=xxxx
    ```

  - Notion token: https://www.notion.so/profile/integrations
  - Notion DB ID: https://www.notion.so/<long_hash_1>?v=<long_hash_2>
    - <long_hash_1>: database ID
    - <long_hash_2>: view ID

```bash
# Export the highlights to Notion page (prompt to enter which book you want)
# Default: export to the page whose ISBN is **0**
python3 ./export-kobo.py --export ./KoboReader.sqlite
# Randomly select 5 highlights and send the email
python3 ./export-kobo.py ./KoboReader.sqlite --email
```

## Installation

### Regular execution (via task scheduler) on WSL

- Program: `C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe`
- Arguments: `-WindowStyle Hidden -ExecutionPolicy Bypass -File "C:\Users\user\kobo.ps1"`
- Settings: Run task as soon as possible after a scheduled start is missed

```bash
# kobo.ps1
wsl -e bash -c "/home/shenjing/export-kobo/kobo.sh"

chmod +x /home/shenjing/export-kobo/kobo.sh
#! /bin/bash
cd /home/shenjing/export-kobo
python3 ./export-kobo.py ./KoboReader.sqlite
```

## TODO

- [] Fuzzy match for book's name
- [] Prettify the email
- [] Highlight Feedback System
  - First prioritize "liked" highlights (select 3 highlights daily).
  - Add remaining highlights from "neutral" feedback if needed.
  - Exclude "disliked" highlights completely from future selections.

## Troubleshooting

## Notes

## Acknowledgments

Special thanks to Alberto Pettarin for the [original version](https://github.com/pettarin/export-kobo).

## License

**export-kobo** is released under the MIT License.



