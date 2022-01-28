# near-slack-bot


redirector testing:
    .env file example content:
        NODE_ENV=development
        SLACK_SIGNING_SECRET=12345
        SLACK_BOT_TOKEN=54321
        PORT=3000
        APIHOST=http://localhost:3000
        CONTRACT_NAME=sub.chokobear.testnet

    dev runtime initialization:
        npm i
        npm run build:js
        npm run start

    wallet auth endpoint
        http://localhost:3000/getAccountId?slackId=mockedSlackId

    send money endpoint
        http://localhost:3000/sendMoney?targetAccountId=sub.chokobear.testnet&amount=0.3


Smart contract deploy

cd contract
./reload_contract <AccountId> <ParentAccountId>

near state contract.sbot.testnet

near view contract.sbot.testnet get_wallet '{"slack_account_id": "test"}'

near call contract.sbot.testnet associate_wallet_with_slack '{"slack_account_id": "test", "near_account_id": "recipient.testnet"}' --accountId sbot.testnet

near call contract.sbot.testnet send_reward '{"slack_account_id": "test"}' --accountId sbot.testnet --deposit 1

near view contract.sbot.testnet get_rewards '{"slack_account_id":"test"}'

near call contract.sbot.testnet withdraw_rewards '{"slack_account_id": "test_recipient"}' --accountId sergey_shpota.testnet 