# QuantConnect Telegram Bot

Unofficial Telegram bot for retrieving data from a QuantConnect live algorithm deployment. Supports Oanda accounts.

## Commands/Features

 * `/get_qc`: Gets the current $ NAV from a QuantConnect deployment.
 * `/get_oanda`: Gets a detailed account summary from an Oanda account, including:
   * NAV
   * Unrealised P&L
   * Realised P&L
   * Margin call %
   * (for each open position) Symbol, Unrealised P&L, Direction, Units

## Getting Started

### Requirements

 * Windows or *NIX instance
 * (if Windows) Visual Studio 2017
 * QuantConnect account and API key
 * Oanda account and API key
 * Telegram account and Bot API token

### Instructions for installation under Windows

1. Clone into directory of choice.
1. Fill out the [`bot-config.json`](https://github.com/Doggie52/QuantConnect-Telegram-Bot/blob/master/QuantConnect-Telegram-Bot/bot-config.json) file.
1. Restore NuGet packages.
1. Compile and run.

### Instructions for installation under *NIX

1. Follow steps to [install Mono](https://www.mono-project.com/download/stable/#download-lin-ubuntu) for your distro, making sure you install `mono-complete`.
1. `sudo apt-get update && sudo apt-get install nuget`
1. Clone into directory of choice, `cd` into this directory.
1. Fill out the [`bot-config.json`](https://github.com/Doggie52/QuantConnect-Telegram-Bot/blob/master/QuantConnect-Telegram-Bot/bot-config.json) file.
1. `nuget restore QuantConnect-Telegram-Bot.sln`
1. `msbuild QuantConnect-Telegram-Bot.sln /p:Configuration=Release`
1. `cd QuantConnect-Telegram-Bot/bin/Release`
1. `mono ./QuantConnect-Telegram-Bot.exe`

If you want to run the process in the background and have it restart automatically if it crashes, replace the last two steps above with the following:

1. `chmod +x ./monitor.sh`
1. `nohup ./monitor.sh &`

### Instructions for Docker deployment

1. Clone into directory of choice, `cd` into this directory.
1. Fill out the [`bot-config.json`](https://github.com/Doggie52/QuantConnect-Telegram-Bot/blob/master/QuantConnect-Telegram-Bot/bot-config.json) file.
1. Build a Docker image. Example for Google Cloud deployment:
   1. `gcloud auth login`, follow steps
   1. `gcloud config set project [PROJECT_ID]`
   1. `gcloud builds submit --tag gcr.io/[PROJECT_ID]/quantconnect-telegram-bot .`
1. Run or deploy image as you see fit.
