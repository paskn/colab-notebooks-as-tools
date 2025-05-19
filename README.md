# Colab Notebooks as Tools

This repository contains a number of Juppyter notebooks with digital methods tools that I created for use with Google Collaboratory. Since a Google account is required for executing a notebook with Colab the notebooks are set up to make use of your private Google Drive for storing sensitive config data as well as your results. You will be prompted for authentification. For storing data a directory *Colab_Data* will be created automatically if it does not yet exist in your Google Drive. Due to this setup these notebooks will not work properly with *Binder*.

To run any these notebooks visit: [colab.research.google.com/](https://colab.research.google.com/). In Google Colab go to File/Open Notebook, select Github and paste "bumatic/colab-notebooks-as-tools" as pointer to this repository. Now a list of available notebooks appears. Select the tool you want to run and open it.

The following tools are currently available:

1. Github Repository Data.ipynb
2. Instagram Scraper.ipynb (provides a Colab UI for [instagram-scraper CLI application](https://github.com/arc298/instagram-scraper))
2. Query Apple App Store and Retrieve Similar Network.ipynb
3. Query Google Play and Retrieve Similar Network.ipynb
4. Scrape Bitchute Platform Recommendations.ipynb
5. Telegram Message Retrieval.ipynb

## GitHub Actions Pipeline for Telegram Message Collection

This repository includes a GitHub Actions pipeline to collect messages from the public channel of PavelDurov on Telegram. The collected messages are stored in the `gdrive/MyDrive/Colab_Data/Data/Telegram` directory in the user's Google Drive.

### How to Run the Pipeline

1. **Fork the Repository**: Fork this repository to your own GitHub account.

2. **Create Telegram API Credentials**:
   - Sign up for Telegram (this step might require a smartphone) and create a so-called application following this link: [Telegram API](https://my.telegram.org/auth).
   - Download the Telegram config template: [telegram_config.ini](http://tiny.cc/telegram-config-template).
   - Add your API ID, API hash, and phone number to the `telegram_config.ini` file using a text editor.
   - Store the `telegram_config.ini` file in a folder named `Colab_Data/Configs` in your Google Drive.

3. **Set Up GitHub Secrets**:
   - Go to the "Settings" tab of your forked repository on GitHub.
   - Click on "Secrets" in the left sidebar.
   - Add the following secrets:
     - `TELEGRAM_API_ID`: Your Telegram API ID.
     - `TELEGRAM_API_HASH`: Your Telegram API hash.
     - `TELEGRAM_PHONE`: Your Telegram phone number.

4. **Run the Workflow**:
   - The workflow is set to run automatically every day at midnight (UTC). You can also trigger it manually from the "Actions" tab in your GitHub repository.

### Workflow File

The GitHub Actions workflow file is located at `/.github/workflows/telegram-message-collector.yml`. It uses the existing code in `Telegram Message Retrieval.ipynb` to retrieve messages from the public channel of PavelDurov.

