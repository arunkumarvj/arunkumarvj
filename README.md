- 👋 Hi, I’m @arunkumarvj
- 👀 I’m interested to  learn new thing in programming
- 🌱 I’m currently learning front end dev
- 📫 How to reach me ...

<!---
arunkumarvj/arunkumarvj is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.

private function downloadFile($url, $destination) {
    // Initialize cURL session
    $ch = curl_init($url);

    // Open file for writing in binary mode
    $fp = fopen($destination, 'wb');  // 'wb' is key here!

    curl_setopt($ch, CURLOPT_FILE, $fp);            // Write directly to file
    curl_setopt($ch, CURLOPT_FOLLOWLOCATION, true); // Follow redirects
    curl_setopt($ch, CURLOPT_TIMEOUT, 20);          // 20-second timeout
    curl_setopt($ch, CURLOPT_FAILONERROR, true);    // Fail on HTTP error

    $success = curl_exec($ch);
    curl_close($ch);
    fclose($fp);

    return $success;
}
--->
