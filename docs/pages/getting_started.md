# Step-by-step guide
Here's a step-by-step guide more suitable for Python beginners.

## Installation
### Python
Download Python from [https://www.python.org/downloads/](https://www.python.org/downloads/) then install.

### Install Poetry
Install Poetry by running this command.

    curl -sSL https://raw.githubusercontent.com/python-poetry/poetry/master/install-poetry.py | python -

You can also check the [Poetry Installation Guide](https://python-poetry.org/docs/#installation).

### Install Dependencies
Install the project dependencies by running poetry install in the source
directory.

    cd axie-scholar-utilities/source
    poetry install

# Setup
## Prepare The Payments File

Create a payments.json file: `axie-scholar-utilities/source/payments.json`

* AccountAddress - the account where the payment will come from
* ScholarPayoutAddress - the scholar's address where the payout will be sent
* ScholarPayout - amount of SLP that the scholar will receive
* TrainerPayoutAddress - (optional) the account of the trainer where the payout will be sent
* TranerPayout - amout of SLP that the trainer will receive
* ManagerPayout - amout of SLP that the manager will receive

```json
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
        }
        {
            "Name": "Scholar 2",
            "AccountAddress": "ronin:<account_address>",
            "ScholarPayoutAddress": "ronin:<scholar_address>",
            "ScholarPayout": 10,
            "TrainerPayoutAddress": "ronin:<trainer_address>",
            "TrainerPayout": 1,
            "ManagerPayout": 9
        }
    ],
    "Donations": [
    ]
}
```

### Generate Secret Key
Create the emtpy secrets.json file by executing this command.

    echo { } > secrets.json

Generate the secrets file by running the following command.

    poetry run python axie_scholar_cli.py generate_secrets payments.json

# Claim and Pay

Claim SLPs by running the following command.

    poetry run python axie_scholar_cli.py claim payments.json secrets.json

Pay your Managers, Trainers, and Scholars by running the following command.

    poetry run python axie_scholar_cli.py payout payments.json secrets.json