# Review dog language tool playground

> [!NOTE]
> Repository to test out `reviewdog/action-languagetool` action behavior
>
> Related to [tuono CI](https://github.com/Valerioageno/tuono/pull/137#pullrequestreview-2455455272)

## Downloading logs

The following script allows to download a zip containing the workflow logs

```sh
REPO="${{ github.repository }}"
RUN_ID="${{ github.run_id }}"

curl -L \
     -H "Accept: application/vnd.github+json" \
     -H "Authorization: Bearer ${{ secrets.GITHUB_TOKEN }}" \
     -H "X-GitHub-Api-Version: 2022-11-28" \
     https://api.github.com/repos/$REPO/actions/runs/$RUN_ID/jobs/$JOB_ID/logs \
     -o job_logs.zip
```

> [!TIP]
> We could use the logs to check for warning / error annotations,
however they wouldn't be accessible within the workflow run, so they should be download from another workflow
after previous workflow completion.
