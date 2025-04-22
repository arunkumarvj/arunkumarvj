- 👋 Hi, I’m @arunkumarvj
- 👀 I’m interested to  learn new thing in programming
- 🌱 I’m currently learning front end dev
- 📫 How to reach me ...

<!---
arunkumarvj/arunkumarvj is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.

private function downloadFile($url, $destination) {
    $readStream = @fopen($url, 'rb'); // Open the file for reading (binary mode)
    if (!$readStream) {
        error_log("❌ Unable to open source URL: $url");
        return false;
    }

    $writeStream = @fopen($destination, 'wb'); // Open the destination file for writing (binary mode)
    if (!$writeStream) {
        error_log("❌ Unable to open destination path: $destination");
        fclose($readStream);
        return false;
    }

    // Stream copy
    $bytesCopied = stream_copy_to_stream($readStream, $writeStream);

    fclose($readStream);
    fclose($writeStream);

    // Confirm file size
    if ($bytesCopied > 0) {
        return true;
    } else {
        error_log("❌ File was created but contains 0 bytes.");
        return false;
    }
}



--->
