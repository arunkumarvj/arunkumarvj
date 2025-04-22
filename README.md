- 👋 Hi, I’m @arunkumarvj
- 👀 I’m interested to  learn new thing in programming
- 🌱 I’m currently learning front end dev
- 📫 How to reach me ...

<!---
arunkumarvj/arunkumarvj is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.


    public function saveDocuments() {
        // Set headers for CORS and JSON response
        header("Access-Control-Allow-Origin: http://localhost:4200");
        header("Access-Control-Allow-Headers: Content-Type");
        header("Access-Control-Allow-Methods: POST, GET, OPTIONS");
        header('Content-Type: application/json');

        // Handle OPTIONS request (preflight)
        if ($_SERVER['REQUEST_METHOD'] === 'OPTIONS') {
            exit; // End the request here for OPTIONS method
        }

        // Get raw POST data
        $json_input = file_get_contents("php://input");

        // If no input data, return error response
        if (empty($json_input)) {
            http_response_code(400);  // Bad Request
            echo json_encode(['status' => 'error', 'message' => 'No input data received']);
            return;
        }

        // Decode the JSON data
        $data = json_decode($json_input, true);

        // Check if the documents data exists
        if (isset($data['documents']) && !empty($data['documents'])) {
            $documents = $data['documents'];

            // Define the path to store the documents on the backend server
            $documents_path = FCPATH . 'documents/Bid_Documents/';
            if (!is_dir($documents_path)) {
                mkdir($documents_path, 0755, true);  // Create directory if it doesn't exist
            }

            // Prepare an array to store document path details
            $document_paths = [];

            // Define the base URL of the frontend server where documents are located
            $base_url = "http://yourfrontendserver.com/";

            // Loop through the documents data and process each document
            foreach ($documents as $document) {
                // Construct the full URL for the document by prepending the base URL
                $document_url = $base_url . $document['DocPathName'];

                // Define the file name and save location
                $document_name = basename($document['DocPathName']);
                $destination_path = $documents_path . $document_name; // Save it with the original name
                
                // Download the document from the constructed URL
                if ($this->downloadFile($document_url, $destination_path)) {
                    // Add the document's new path to the array
                    $document_paths[] = [
                        'BidDocId' => $document['BidDocId'],
                        'DocName' => $document['DocName'],
                        'DocTypeDesc' => $document['DocTypeDesc'],
                        'DocPathName' => 'documents/Bid_Documents/' . $document_name, // New path after saving
                        'CreatedUserId' => $document['CreatedUserId'],
                        'CreatedDate' => $document['CreatedDate']
                    ];
                }
            }

            // Save the document path data in a JSON file
            $json_file_path = FCPATH . 'export/documents.json';
            file_put_contents($json_file_path, json_encode($document_paths, JSON_PRETTY_PRINT));

            // Send a success response
            http_response_code(200);  // OK
            echo json_encode(['status' => 'success', 'message' => 'Documents saved successfully']);
        } else {
            // Send error response if no documents provided
            http_response_code(400);  // Bad Request
            echo json_encode(['status' => 'error', 'message' => 'No documents data provided']);
        }
    }

    // Function to download file from a URL and save it to the server
    private function downloadFile($url, $destination) {
        // Use cURL to fetch the file
        $ch = curl_init();
        $timeout = 5; // Set timeout to 5 seconds
        curl_setopt($ch, CURLOPT_URL, $url);
        curl_setopt($ch, CURLOPT_RETURNTRANSFER, 1);
        curl_setopt($ch, CURLOPT_TIMEOUT, $timeout);
        $data = curl_exec($ch);
        curl_close($ch);

        // If the file is successfully downloaded, save it
        if ($data) {
            file_put_contents($destination, $data);
            return true;
        }

        return false;
    }
--->
