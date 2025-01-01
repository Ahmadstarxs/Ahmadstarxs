CURL *hnd = curl_easy_init();

curl_easy_setopt(hnd, CURLOPT_CUSTOMREQUEST, "GET");
curl_easy_setopt(hnd, CURLOPT_WRITEDATA, stdout);
curl_easy_setopt(hnd, CURLOPT_URL, "https://www.virustotal.com/api/v3/files/id/download");

struct curl_slist *headers = NULL;
headers = curl_slist_append(headers, "accept: application/json");
curl_easy_setopt(hnd, CURLOPT_HTTPHEADER, headers);

CURLcode ret = curl_easy_perform(hnd);

<!---
Ahmadstarxs/Ahmadstarxs is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
name: Issue Management
on:
  issues:
    types: [opened, edited, reopened]

permissions:
  issues: write
  contents: read

jobs:
  manage-issue:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4

      - name: AI Issue Manager
        uses: xuezhaojun/ai-issue-manager@v1
        with:
          openai_api_key: ${{ secrets.OPENAI_API_KEY }}
          openai_api_url: "https://api.openai.com/v1"
          github_token: ${{ secrets.GITHUB_TOKEN }}
          model: "gpt-4"
          condition: |
            The issue should:
            1. Have a clear description of the problem
            2. Include steps to reproduce
            3. Specify the expected behavior
          actions: "comment,label_add"
          action_comment: "Thank you for your detailed bug report!"
          action_labels: "bug,needs-triage"
