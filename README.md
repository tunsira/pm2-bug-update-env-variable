# PM2 Bug - Reloading environment variables with zero downtime

Link: https://github.com/Unitech/pm2/issues/3192#issuecomment-409002530

# Steps

Install dependencies

    npm i

Remove stale logs if there are any

    rm -f *.log

Start pm2 with the staging environment

    npx pm2 start ecosystem.config.js --env staging

Reload app with zero downtime in a different environment. Also tried `restart`.

    npx pm2 reload all --env production --update-env

Check app-0.log

    cat app*.log

You will see

    Server running at http://127.0.0.1:8000/
    staging
    Server running at http://127.0.0.1:8000/
    staging

Instead of

    Server running at http://127.0.0.1:8000/
    staging
    Server running at http://127.0.0.1:8000/
    production

