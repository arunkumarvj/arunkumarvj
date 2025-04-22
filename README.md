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

        // Create directory if it doesn't exist
        if (!is_dir($dir)) {
            if (!mkdir($dir, 0777, true)) {
                $results[] = [
                    'DocName' => $doc['DocName'],
                    'status' => 'error',
                    'message' => "Failed to create directory: $dir"
                ];
                continue;
            }
        }

        // Set headers to simulate browser request
        $headers = [
            'User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64)',
            'Accept: */*',
            'Referer: ' . $url,
            'Origin: http://yourdomain.com' // Optional - replace with your actual frontend
        ];

        // Initialize cURL
        $ch = curl_init($url);
        curl_setopt_array($ch, [
            CURLOPT_RETURNTRANSFER => true,
            CURLOPT_FOLLOWLOCATION => true,
            CURLOPT_TIMEOUT => 30,
            CURLOPT_SSL_VERIFYPEER => false,
            CURLOPT_SSL_VERIFYHOST => false,
            CURLOPT_HEADER => true,
            CURLOPT_HTTPHEADER => $headers
        ]);

        $response = curl_exec($ch);
        $curlErr = curl_error($ch);
        $httpCode = curl_getinfo($ch, CURLINFO_HTTP_CODE);
        $headerSize = curl_getinfo($ch, CURLINFO_HEADER_SIZE);
        curl_close($ch);

        $responseHeaders = substr($response, 0, $headerSize);
        $body = substr($response, $headerSize);

        if ($httpCode === 200 && $body) {
            file_put_contents($savePath, $body);
            $results[] = [
                'DocName' => $doc['DocName'],
                'status' => 'success',
                'message' => "Saved to $savePath"
            ];
        } else {
            $results[] = [
                'DocName' => $doc['DocName'],
                'status' => 'error',
                'message' => "Download failed from: $url\nHTTP Code: $httpCode\nError: $curlErr\nHeaders:\n$responseHeaders"
            ];
        }
    }

    header('Content-Type: application/json');
    echo json_encode($results);
}

--->
