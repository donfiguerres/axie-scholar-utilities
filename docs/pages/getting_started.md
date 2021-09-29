# Step-by-step guide
Here's a step-by-step guide more suitable for Python beginners.

## Installation
### Python
Download Python from [https://www.python.org/downloads/](https://www.python.org/downloads/).

### Install Poetry
Install Poetry by running this command.

    curl -sSL https://raw.githubusercontent.com/python-poetry/poetry/master/install-poetry.py | python -

See the [GitHub repo](https://github.com/python-poetry/poetry) If you want to
learn more about Poetry.

### Install Rependencies
Install the project dependencies by running poetry install in the source
directory.

    cd axie-scholar-utilities/source
    poetry install

# Setup
## Prepare The Payments File

Create a payments.json file.

```
{
    "Manager": "ronin:<Manager address here>",
    "Scholars":[
        {
            "Name": "Scholar 1",
            "AccountAddress": "ronin:<account_address>",
            "ScholarPayoutAddress": "ronin:<scholar_address>",
            "ScholarPayout": 10,
            "TrainerPayoutAddress": "ronin:<trainer_address>",
            "TrainerPayout": 1,
            "ManagerPayout": 9
        },
        {...},
        ...
    ],
    "Donations": [
    ]
}
```

### Generate Secret Key
Generate the secrets file by running the following command.

    poetry run python axie_scholar_cli.py generate_secrets payments.json

# Claim and Pay

Claim SLPs by running the following command.

    poetry run python axie_scholar_cli.py claim payments.json secrets.json

Pay your Managers, Trainers, and Scholars by running the following command.

    poetry run python axie_scholar_cli.py payout payments.json secrets.json