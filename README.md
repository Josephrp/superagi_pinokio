# superagi.com-autonomous-agents-hackathon
Team Tonic Super AGI Autonomous Agents Hackathon GitHub Repository.

#### 8/19/2023 From Cocktail Peanut -

### Install (as yet "unreleased") Pinokio.Computer in AWS :

git clone https://github.com/pinokiocomputer/pinokiod

cd pinokiod

npm install

npm start

then use pinokio here : 

open http://localhost:4200/

## DRAFT PINOKIO SCRIPT FROM KEITH 8/17/2023

{
    "run": [
        {
            "method": "shell.run",
            "params": {
                "message": "git clone git clone https://github.com/TransformerOptimus/SuperAGI.git superaGI",
                "path": "./"
            }
        },
        {
            "method": "input",
            "params": {
                "title": "Settings",
                "form": [
                    {
                        "title": "OpenAI API KEY",
                        "key": "OPENAI_API_KEY",
                        "description": "Find your OpenAI API key <a target='_blank' href= 'https://platform.openai.com/account/api-keys'>here</a>"
                    },
                    {
                        "title": "Google API key",
                        "key": "GOOGLE_API_KEY",
                        "description": "Find your goole API key <a target='_blank' href= 'https://console.cloud.google.com'>here</a>"
                    },
                    {
                        "title": "Google Programmable Search Engine",
                        "key": "SEARCH_ENGINE_ID",
                        "description": "Find your goole API key <a target='_blank' href= 'https://console.cloud.google.com'>here</a>"
                    },
                    {
                        "title": "Pinecone Environment",
                        "key": "PINECONE_ENVIRONMENT"
                    },
                    {
                        "title": "Pinecone API KEY",
                        "key": "PINECONE_API_KEY"
                    }
                ]
            }
        },
        {
            "method": "fs.write",
            "params": {
                "path": "./superagi",
                "text": [
                    "PINECONE_API_KEY={{input.PINECONE_API_KEY}}",
                    "PINECONE_ENVIRONMENT={{input.PINECONE_ENVIRONMENT}}",
                    "",
                    "OPENAI_API_KEY={{input.OPENAI_API_KEY}}",
                    "PALM_API_KEY={{input.PALM_API_KEY}}",
                    "",
                    "OPENAI_API_BASE=\"https://api.openai.com/v1\"",
                    "",
                    "MODEL_NAME=\"gpt-3.5-turbo-0301\"",
                    "RESOURCES_SUMMARY_MODEL_NAME=\"gpt-3.5-turbo\"",
                    "MAX_TOOL_TOKEN_LIMIT=800",
                    "MAX_MODEL_TOKEN_LIMIT=4032",
                    "",
                    "DB_NAME=super_agi_main",
                    "POSTGRES_URL=super__postgres",
                    "DB_USERNAME=superagi",
                    "DB_PASSWORD=password",
                    "REDIS_URL=\"super__redis:6379\"",
                    "",
                    "STORAGE_TYPE=\"FILE\"",
                    "",
                    "TOOLS_DIR=\"superagi/tools\"",
                    "RESOURCES_INPUT_ROOT_DIR=workspace/input/{agent_id}",
                    "RESOURCES_OUTPUT_ROOT_DIR=workspace/output/{agent_id}/{agent_execution_id}",
                    "",
                    "BUCKET_NAME=",
                    "INSTAGRAM_TOOL_BUCKET_NAME=",
                    "AWS_ACCESS_KEY_ID=",
                    "AWS_SECRET_ACCESS_KEY=",
                    "",
                    "ENV='DEV'",
                    "JWT_SECRET_KEY='secret'",
                    "expiry_time_hours=1",
                    "",
                    "GITHUB_CLIENT_ID=",
                    "GITHUB_CLIENT_SECRET=",
                    "FRONTEND_URL=\"http://localhost:3000\"",
                    "",
                    "ENCRYPTION_KEY=secret",
                    "WEAVIATE_USE_EMBEDDED=true",
                    "",
                    "GOOGLE_API_KEY={{input.GOOGLE_API_KEY}}",
                    "SEARCH_ENGINE_ID={{input.SEARCH_ENGINE_ID}}",
                    "",
                    "SERP_API_KEY={{input.SERP_API_KEY}}",
                    "",
                    "EMAIL_ADDRESS={{input.EMAIL_ADDRESS}}",
                    "EMAIL_PASSWORD={{input.EMAIL_APP_PASSWORD}}",
                    "EMAIL_SMTP_HOST=smtp.gmail.com",
                    "EMAIL_SMTP_PORT=587",
                    "EMAIL_IMAP_SERVER=imap.gmail.com",
                    "EMAIL_SIGNATURE='Email sent by SuperAGI'",
                    "EMAIL_DRAFT_MODE_WITH_FOLDER={{input.YOUR_DRAFTS_FOLDER}}",
                    "EMAIL_ATTACHMENT_BASE_PATH={{input.YOUR_DIRECTORY_FOR_EMAIL_ATTACHMENTS}}",
                    "",
                    "GITHUB_USERNAME={{input.GITHUB_USERNAME}}",
                    "GITHUB_ACCESS_TOKEN={{input.GITHUB_ACCESS_TOKEN}}",
                    "",
                    "JIRA_INSTANCE_URL={{input.JIRA_INSTANCE_URL}}",
                    "JIRA_USERNAME={{input.JIRA_EMAIL}}",
                    "JIRA_API_TOKEN={{input.JIRA_API_TOKEN}}",
                    "",
                    "SLACK_BOT_TOKEN={{input.SLACK_BOT_TOKEN}}",
                    "",
                    "STABILITY_API_KEY={{input.STABILITY_API_KEY}}",
                    "ENGINE_ID=\"stable-diffusion-xl-beta-v2-2-2\""
                ],
                "join": "{{os.EOL}}"
            }
        },
        {
            "method": "shell.run",
            "params": {
                "message": "cp config_template.yaml config.yaml",
                "path": "./superagi"
            }
        },
        {
            "method": "shell.run",
            "params": {
                "message": "docker-compose up --build",
                "path": "./superagi"
            }
        },
        {
            "method": "notify",
            "params": {
                "html": "superagi installation complete! Click here to get started!",
                "href": "http://localhost:3000"
            }
        }
    ]
}
