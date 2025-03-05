# Telegram Referral Bot

## Overview
This script automates the process of adding Telegram accounts as referrals to bots using your invite code. It emulates the **/start** command with an additional parameter for the referral code.

## Features
- Automatically adds Telegram accounts as referrals.
- Supports multiple accounts.
- Optionally joins required channels.
- Adjustable delay settings between account actions.
- Supports proxy usage for additional security.

## Installation
1. Clone the repository:
   ```sh
   git clone https://github.com/svtcore/telegram-referral-bot.git
   cd telegram-referral-bot
   ```
2. Install the required dependencies:
   ```sh
   pip install -r requirements.txt
   ```

## Configuration
1. Open the `.env` file and modify the parameters according to your needs:

   **.env File Parameters:**
   - `BOT_NAME`: The bot's public name (without `@`). Example: `example_random_bot`
   - `COUNT`: Number of accounts to use.
   - `REFER_ID`: Your referral ID from the bot (from `t.me/example_random_bot?start=12345`, set only `12345`).
   - `CHANNEL_NAME`: The username of the channel to join *(optional)*.
   - `DELAY_MIN`: Minimum delay (in seconds) between actions.
   - `DELAY_MAX`: Maximum delay (in seconds) between actions.

   **Example `.env` File:**
   ```ini
   BOT_NAME=my_new_coin_bot
   COUNT=5
   REFER_ID=111222333
   CHANNEL_NAME=my_new_coin_channel
   DELAY_MIN=10
   DELAY_MAX=15
   ```

## Setup Steps
### 1. Retrieve Telegram API Credentials
- Go to [my.telegram.org](https://my.telegram.org) and create a new application.
- Obtain your `API_ID` and `API_HASH`.

### 2. Create a File for Account Credentials
Create a file named `accounts.txt` and input the following format:

   **Example for API credentials:**
   ```
   SESSION_NAME:API_ID:API_HASH
   MY_ACCOUNT_1:11223344:d54d1702ad0f8326224b817c796763c9
   ```
   **Example for Pyrogram string sessions:**
   ```
   Ag1C11H4AJxbIL5Cr4xovee6MlhrE0XYJud9h_w4RbADPko_...
   ```

### 3. (Optional) Set Up a Proxy
Create a `proxies.txt` file:
   ```
   NO PROXY (leave file empty)
   IP:PORT
   IP:PORT:LOGIN:PASSWORD
   ```

### 4. Authorize Telegram Accounts
Run the following command to create session files and authenticate accounts:
   ```sh
   python bot.py --auth --tokens accounts.txt
   ```
After authorization, session files will be stored in the `sessions/` folder.

### 5. Start Adding Referrals
Run the script to begin inviting accounts:
   ```sh
   python bot.py --run --tokens accounts.txt
   ```
   **Alternative commands:**
   - With string sessions:
     ```sh
     python bot.py --run --strings --tokens accounts.txt
     ```
   - With proxy support:
     ```sh
     python bot.py --run --tokens accounts.txt --proxies proxies.txt
     ```
   - If the bot requires joining a channel:
     ```sh
     python bot.py --run --tokens accounts.txt --channel
     ```

📌 **Note:** Ensure that `accounts.txt` and `proxies.txt` are in the project root directory.

## Contributing
Pull requests are welcome. For major changes, open an issue to discuss proposed updates. If the script returns an error, please report it with the error message.

## Libraries Used
- [Pyrogram](https://github.com/pyrogram/pyrogram)
- [python-dotenv](https://github.com/theskumar/python-dotenv)

## Disclaimer
This script is for educational purposes only. The author is not responsible for misuse.

