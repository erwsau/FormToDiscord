const POST_URL = "https://discord.com/api/webhooks/xxxxxxxxx/xxxxxxxxxxxxxxxx";

function onSubmit(e) {
    const response = e.response.getItemResponses();
    let items = [];

    for (const responseAnswer of response) {
        const question = responseAnswer.getItem().getTitle();
        const answer = responseAnswer.getResponse();
        let parts = []

        try {
            parts = answer.match(/[\s\S]{1,1024}/g) || [];
        } catch (e) {
            parts = answer;
        }

        if (!answer) {
            continue;
        }

        for (const [index, part] of Object.entries(parts)) {
            if (index == 0) {
                items.push({
                    "name": question,
                    "value": part,
                    "inline": false
                });
            } else {
                items.push({
                    "name": question.concat(" (cont.)"),
                    "value": part,
                    "inline": false
                });
            }
        }
    }

    const options = {
        "method": "post",
        "headers": {
            "Content-Type": "application/json",
        },
        "payload": JSON.stringify({
            "content": "‌",
            "embeds": [{
                "title": "Candidature",
              "color": 4394528,
                "fields": items,
                    "thumbnail": {
      "url": "https://cdn.discordapp.com/attachments/xxxxxxxx/xxxxxxxxxx/LogoRed.png"},
                "footer": {
                    "text": "réagissez avec ⌛ ou ❌"
                }
            }]
        })
    };

    UrlFetchApp.fetch(POST_URL, options);
};
