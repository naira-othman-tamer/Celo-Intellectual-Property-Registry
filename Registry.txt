// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

/**
 * @title Registry
 * @dev Intellectual Property Registry for timestamping and storing ideas on the Celo blockchain
 * @notice This contract allows users to register their intellectual property with immutable timestamps
 */
contract Registry {
    
    // ============================================
    // STATE VARIABLES
    // ============================================
    
    /// @notice Counter for total number of records
    uint256 public recordCount;
    
    /// @notice Mapping from record ID to Record struct
    mapping(uint256 => Record) public records;
    
    // ============================================
    // STRUCTS
    // ============================================
    
    /// @notice Structure to store intellectual property record
    struct Record {
        address owner;          // Address of the person who registered the IP
        uint256 timestamp;      // Block timestamp when the record was created
        string title;           // Title of the intellectual property
        string ownerName;       // Name of the owner
        string data;            // Description or content hash (e.g., SHA-256)
    }
    
    // ============================================
    // EVENTS
    // ============================================
    
    /// @notice Emitted when a new record is registered
    /// @param id The unique ID of the registered record
    /// @param owner The address of the owner who registered the record
    /// @param timestamp The timestamp when the record was registered
    event RecordRegistered(
        uint256 indexed id,
        address indexed owner,
        uint256 timestamp
    );
    
    // ============================================
    // FUNCTIONS
    // ============================================
    
    /**
     * @notice Register a new intellectual property record
     * @param _title The title of the work being registered
     * @param _ownerName The name of the owner
     * @param _data The description or content hash of the IP
     * @return The unique ID of the newly created record
     */
    function registerRecord(
        string memory _title,
        string memory _ownerName,
        string memory _data
    ) public returns (uint256) {
        // Validate inputs
        require(bytes(_title).length > 0, "Title cannot be empty");
        require(bytes(_ownerName).length > 0, "Owner name cannot be empty");
        require(bytes(_data).length > 0, "Data cannot be empty");
        
        // Increment record count
        recordCount++;
        
        // Create new record
        records[recordCount] = Record({
            owner: msg.sender,
            timestamp: block.timestamp,
            title: _title,
            ownerName: _ownerName,
            data: _data
        });
        
        // Emit event
        emit RecordRegistered(recordCount, msg.sender, block.timestamp);
        
        return recordCount;
    }
    
    /**
     * @notice Retrieve a record by its ID
     * @param _id The unique ID of the record to retrieve
     * @return owner The address of the record owner
     * @return timestamp The timestamp when the record was created
     * @return title The title of the work
     * @return ownerName The name of the owner
     * @return data The description or content hash
     */
    function getRecord(uint256 _id) public view returns (
        address owner,
        uint256 timestamp,
        string memory title,
        string memory ownerName,
        string memory data
    ) {
        require(_id > 0 && _id <= recordCount, "Invalid record ID");
        
        Record memory record = records[_id];
        
        return (
            record.owner,
            record.timestamp,
            record.title,
            record.ownerName,
            record.data
        );
    }
    
    /**
     * @notice Get all records registered by a specific owner
     * @param _owner The address of the owner
     * @return Array of record IDs owned by the specified address
     */
    function getRecordsByOwner(address _owner) public view returns (uint256[] memory) {
        // First, count how many records belong to this owner
        uint256 ownerRecordCount = 0;
        for (uint256 i = 1; i <= recordCount; i++) {
            if (records[i].owner == _owner) {
                ownerRecordCount++;
            }
        }
        
        // Create array with the correct size
        uint256[] memory ownerRecords = new uint256[](ownerRecordCount);
        
        // Populate the array
        uint256 currentIndex = 0;
        for (uint256 i = 1; i <= recordCount; i++) {
            if (records[i].owner == _owner) {
                ownerRecords[currentIndex] = i;
                currentIndex++;
            }
        }
        
        return ownerRecords;
    }
    
    /**
     * @notice Check if a record exists
     * @param _id The record ID to check
     * @return True if the record exists, false otherwise
     */
    function recordExists(uint256 _id) public view returns (bool) {
        return _id > 0 && _id <= recordCount;
    }
    
    /**
     * @notice Get the total number of registered records
     * @return The total count of records
     */
    function getTotalRecords() public view returns (uint256) {
        return recordCount;
    }
}
