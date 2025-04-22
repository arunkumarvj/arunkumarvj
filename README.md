- 👋 Hi, I’m @arunkumarvj
- 👀 I’m interested to  learn new thing in programming
- 🌱 I’m currently learning front end dev
- 📫 How to reach me ...

<!---
arunkumarvj/arunkumarvj is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.

public function saveDocuments() {
    $input = json_decode(file_get_contents("php://input"), true);

    foreach ($input as $doc) {
        // Initialize cURL to download the file
        $ch = curl_init($doc['fullDocURL']);
        
        // Set cURL options to handle the file download
        curl_setopt($ch, CURLOPT_RETURNTRANSFER, true);   // To capture the response as string
        curl_setopt($ch, CURLOPT_FOLLOWLOCATION, true);   // Follow redirects if any
        curl_setopt($ch, CURLOPT_HEADER, true);           // Capture headers as well
        curl_setopt($ch, CURLOPT_NOBODY, false);          // We need the body (file content)
        
        // Execute the cURL request
        $response = curl_exec($ch);
        
        if (curl_errno($ch)) {
            log_message('error', "cURL Error: " . curl_error($ch));
            curl_close($ch);
            continue; // Skip to next document if there's an error
        }
        
        // Get the HTTP code to check for success
        $httpCode = curl_getinfo($ch, CURLINFO_HTTP_CODE);
        
        if ($httpCode != 200) {
            log_message('error', "Download failed from: " . $doc['fullDocURL'] . "\nHTTP Code: $httpCode\nError: " . curl_error($ch));
            curl_close($ch);
            continue; // Skip to next document if the download fails
        }

        // Extract the headers
        $header_size = curl_getinfo($ch, CURLINFO_HEADER_SIZE);
        $fileContent = substr($response, $header_size); // Extract the actual file content
        
        // Close the cURL session
        curl_close($ch);

        // Build the destination path
        $savePath = FCPATH . $doc['DocPathName'];
        $dir = dirname($savePath);

        // Create directories if they don't exist
        if (!is_dir($dir)) {
            mkdir($dir, 0777, true);
        }

        // Save the file to the destination path
        file_put_contents($savePath, $fileContent);
    }

    echo json_encode(['status' => 'success', 'message' => 'Documents saved']);
}

http://www.vertexmanagementsystem.com/VertexAPI/documents/Bid_Documents/ABA2/5367f75df33688a-553297-1001811pdf.pdf

--->
