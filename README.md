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
