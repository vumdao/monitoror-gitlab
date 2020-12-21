![Alt Text](https://dev-to-uploads.s3.amazonaws.com/i/34asre31pk0vefq9189r.jpg)

This post describe how to add gitlab pipeline jobs to monitoror dashboard
![Alt Text](https://dev-to-uploads.s3.amazonaws.com/i/6ddieunniujpoqbkjup6.png)

##GITLAB-PIPELINE

###Add configs to env
```
MO_CONFIG_GITLAB=/monitoror/config_gitlab.json
MO_MONITORABLE_GITLAB_URL=https://gitlab.com
MO_MONITORABLE_GITLAB_TOKEN=GwLzYzJh4bezFctgwQDY
MO_MONITORABLE_GITLAB_TIMEOUT=5000
How to generate gitlab token
```

###Create config_gitlab.json
- Group a project as a tile group and branches are its element
- Add HTTP-RAW for site demo to monitoring its version (meta.txt)


```
{
   "version":"2.0",
   "columns":2,
   "tiles":[
      {
         "type":"GROUP",
         "label":"MyProject - CI Jobs Running",
         "rowSpan":4,
         "tiles":[
            {
               "type":"GITLAB-PIPELINE",
               "label":"MyProject",
               "params":{
                  "projectId":21808445,
                  "ref":"master"
               }
            },
            {
               "type":"GITLAB-PIPELINE",
               "label":"MyProject",
               "params":{
                  "projectId":144,
                  "ref":"develop"
               }
            }
         ]
      },
      {
         "type":"GROUP",
         "label":"Serverless - CI Jobs Running",
         "rowSpan":4,
         "tiles":[
            {
               "type":"GITLAB-PIPELINE",
               "label":"Serverless",
               "params":{
                  "projectId":167,
                  "ref":"master"
               }
            },
            {
               "type":"GITLAB-PIPELINE",
               "label":"Serverless",
               "params":{
                  "projectId":167,
                  "ref":"develop"
               }
            }
         ]
      }
   ]
}
```

{% github vumdao/monitoror %}
###Generate config_gitlab.json with multiple projects and multiple branches
* Use script to auto generate
`python gen_conf.py`
![Alt Text](https://dev-to-uploads.s3.amazonaws.com/i/e85yyzhww2fokf1lyzbf.png)
