- 👋 Hi, I’m @arunkumarvj
- 👀 I’m interested to  learn new thing in programming
- 🌱 I’m currently learning front end dev
- 📫 How to reach me ...

<!---
arunkumarvj/arunkumarvj is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.

private function downloadFile($url, $destination) {
    $ch = curl_init();

    // Custom headers to mimic a browser
    $headers = [
        "User-Agent: Mozilla/5.0",
        "Accept: application/pdf",
    ];

    curl_setopt($ch, CURLOPT_URL, $url);
    curl_setopt($ch, CURLOPT_HTTPHEADER, $headers);
    curl_setopt($ch, CURLOPT_RETURNTRANSFER, true);
    curl_setopt($ch, CURLOPT_FOLLOWLOCATION, true); // Follow redirects
    curl_setopt($ch, CURLOPT_TIMEOUT, 30);

    $data = curl_exec($ch);
    $httpCode = curl_getinfo($ch, CURLINFO_HTTP_CODE);
    $contentType = curl_getinfo($ch, CURLINFO_CONTENT_TYPE);
    $error = curl_error($ch);

    curl_close($ch);

    // Log the content type for debugging
    error_log("Status: $httpCode, Type: $contentType");

    // Save if it's a PDF and response is OK
    if ($data !== false && $httpCode === 200 && strpos($contentType, 'application/pdf') !== false) {
        file_put_contents($destination, $data);
        return true;
    }

    error_log("Failed to download: $url. Error: $error");
    return false;
}


--->
