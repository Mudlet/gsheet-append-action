# gsheets-append-action

## Inputs

| Input              | Required | Default | Description                                                                                                                                                                        |
| ------------------ | :------: | :-----: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `GOOGLE_USER_MAIL` |  `true`  |         | The user ID to authenticate the service account user.                                                                                                                              |
| `GOOGLE_USER_KEY`  |  `true`  |         | The users private key to authenticate the service account user.                                                                                                                    |
| `SPREADSHEET`      |  `true`  |         | The spreadsheet ID to append the data to.                                                                                                                                          |
| `DATA_FILE_PATH`   | `false`  |         | The csv file containing the data to upload. Use either this or DATA_ENV_NAME. **NOTE**: If DATA_FILE_PATH is configured, DATA_ENV_NAME will be ignored.                            |
| `DATA_ENV_NAME`    | `false`  |         | The environment variable containing the data to upload in CSV format. Use either this or DATA_FILE_PATH. **NOTE**: If DATA_FILE_PATH is configured, DATA_ENV_NAME will be ignored. |
| `TABLE_START_CELL` | `false`  |   A1    | The cell that defines the "table anchor" in the format `sheetName!A1`.                                                                                                             |
| `UPDATE`           | `false`  |  false  | Update or append data.                                                                                                                                                             |

## About private key

If you use GitHub Secrets to store a JSON private key, be mindful that you need
to change all embedded `\n` linebreaks with real ones.

Given your JSON's `private_key` content is along the lines of:

```text
-----BEGIN PRIVATE KEY-----\nBLABLABLABLABLA\nBLABLABLABLABLA\n-----END PRIVATE KEY-----\n
```

Change it to:

```text
-----BEGIN PRIVATE KEY-----
BLABLABLABLABLA
BLABLABLABLABLA
-----END PRIVATE KEY-----
```

And use that as your `GOOGLE_USER_KEY` input.

Credit: https://github.com/dibenlloch/google-sheets-secrets-action

## For action authors

After editing the action, run `npm ci` to regenerate `dist/` and put edits into
effect.
