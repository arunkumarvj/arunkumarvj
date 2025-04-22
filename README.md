- 👋 Hi, I’m @arunkumarvj
- 👀 I’m interested to  learn new thing in programming
- 🌱 I’m currently learning front end dev
- 📫 How to reach me ...

<!---
arunkumarvj/arunkumarvj is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.

public function saveDocuments()
{
    $docs = json_decode(file_get_contents("php://input"), true);
    $response = [];

    foreach ($docs as $doc) {
        $docName = $doc['DocName'];
        $fileUrl = $doc['fullDocURL'];
        $saveRelativePath = $doc['DocPathName']; // example: documents/Bid_Documents/ABA2/file.pdf
        $saveFullPath = FCPATH . $saveRelativePath;

        // Create directory if it doesn't exist
        $saveDir = dirname($saveFullPath);
        if (!is_dir($saveDir)) {
            mkdir($saveDir, 0777, true);
        }

        // Download file
        $fileContent = @file_get_contents($fileUrl);

        if ($fileContent === false) {
            $response[] = [
                'DocName' => $docName,
                'status' => 'error',
                'message' => "Failed to download: $fileUrl"
            ];
            continue;
        }

        // Save file to server
        if (file_put_contents($saveFullPath, $fileContent)) {
            $response[] = [
                'DocName' => $docName,
                'status' => 'success',
                'message' => "Saved to $saveRelativePath"
            ];
        } else {
            $response[] = [
                'DocName' => $docName,
                'status' => 'error',
                'message' => "Failed to save file on server"
            ];
        }
    }

    // Final JSON response back to frontend
    header('Content-Type: application/json');
    echo json_encode($response);
}



--->
