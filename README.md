- 👋 Hi, I’m @arunkumarvj
- 👀 I’m interested to  learn new thing in programming
- 🌱 I’m currently learning front end dev
- 📫 How to reach me ...

<!---
arunkumarvj/arunkumarvj is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.

public function saveDocuments() {
    $input = json_decode(file_get_contents("php://input"), true);
    $results = [];

    foreach ($input as $doc) {
        $url = $doc['fullDocURL'];
        $savePath = FCPATH . $doc['DocPathName'];
        $dir = dirname($savePath);

        // Ensure directory exists
        if (!is_dir($dir)) {
            if (!mkdir($dir, 0777, true)) {
                log_message('error', "Failed to create directory: $dir");
                $results[] = [
                    'DocName' => $doc['DocName'],
                    'status' => 'error',
                    'message' => "Failed to create directory: $dir"
                ];
                continue;
            }
        }

        // Use cURL for downloading
        $ch = curl_init($url);
        curl_setopt($ch, CURLOPT_RETURNTRANSFER, true);
        curl_setopt($ch, CURLOPT_FOLLOWLOCATION, true);
        curl_setopt($ch, CURLOPT_TIMEOUT, 30);
        curl_setopt($ch, CURLOPT_SSL_VERIFYPEER, false);
        curl_setopt($ch, CURLOPT_SSL_VERIFYHOST, false);
        $fileContent = curl_exec($ch);
        $httpCode = curl_getinfo($ch, CURLINFO_HTTP_CODE);
        $curlErr = curl_error($ch);
        curl_close($ch);

        if ($httpCode === 200 && $fileContent) {
            file_put_contents($savePath, $fileContent);
            $results[] = [
                'DocName' => $doc['DocName'],
                'status' => 'success',
                'message' => "Saved to $savePath"
            ];
        } else {
            log_message('error', "Failed to download file: $url - $curlErr");
            $results[] = [
                'DocName' => $doc['DocName'],
                'status' => 'error',
                'message' => "Failed to download: $url. Error: $curlErr"
            ];
        }

        // Optional: Save metadata in DB
    }

    header('Content-Type: application/json');
    echo json_encode($results);
}


--->
