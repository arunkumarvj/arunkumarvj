- 👋 Hi, I’m @arunkumarvj
- 👀 I’m interested to  learn new thing in programming
- 🌱 I’m currently learning front end dev
- 📫 How to reach me ...

<!---
arunkumarvj/arunkumarvj is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.

private function downloadFile($url, $destination) {
    $fp = fopen($destination, 'wb');
    if (!$fp) {
        echo "❌ Failed to open file for writing: $destination";
        return false;
    }

    $ch = curl_init($url);

    curl_setopt($ch, CURLOPT_FILE, $fp); // Stream directly to file
    curl_setopt($ch, CURLOPT_HEADER, 0); // No headers in output
    curl_setopt($ch, CURLOPT_FOLLOWLOCATION, true); // Follow redirects
    curl_setopt($ch, CURLOPT_TIMEOUT, 30); // Timeout after 30s
    curl_setopt($ch, CURLOPT_FAILONERROR, true); // Return false on HTTP errors
    curl_setopt($ch, CURLOPT_SSL_VERIFYPEER, false); // If HTTPS and self-signed

    $success = curl_exec($ch);

    if (!$success) {
        $error = curl_error($ch);
        echo "❌ cURL error while downloading $url: $error";
    }

    curl_close($ch);
    fclose($fp);

    return $success;
}

--->
