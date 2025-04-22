- 👋 Hi, I’m @arunkumarvj
- 👀 I’m interested to  learn new thing in programming
- 🌱 I’m currently learning front end dev
- 📫 How to reach me ...

<!---
arunkumarvj/arunkumarvj is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.

private function downloadFile($url, $destination) {
    $ch = curl_init($url);
    $fp = fopen($destination, 'w+b'); // Ensure binary mode

    curl_setopt_array($ch, [
        CURLOPT_FILE => $fp,
        CURLOPT_HEADER => 0,
        CURLOPT_FOLLOWLOCATION => true,
        CURLOPT_TIMEOUT => 30,
        CURLOPT_FAILONERROR => true,
        CURLOPT_SSL_VERIFYPEER => false,
        CURLOPT_SSL_VERIFYHOST => false
    ]);

    $success = curl_exec($ch);

    if (!$success) {
        error_log('cURL error: ' . curl_error($ch));
    }

    curl_close($ch);
    fclose($fp);

    return $success;
}


--->
