# Processing Contracts

Initial contracts between system components.

---

## Contract Definitions

### ProcessingJob

**Purpose:** Represents a single processing request from submission to completion.

**Input:**
- `jobId`: Unique identifier
- `inputDataset`: Reference to InputDataset
- `operations`: Array of ProcessingOperation
- `parameters`: ProcessingParameters
- `aoi`: Area of Interest (optional)
- `priority`: Job priority level
- `metadata`: User-defined metadata

**Output:**
- `jobId`: Same identifier
- `status`: JobStatus (QUEUED, RUNNING, COMPLETED, FAILED, CANCELLED)
- `tasks`: Array of Task references
- `result`: ProcessingResult (on completion)
- `error`: ProcessingError (on failure)
- `createdAt`: Timestamp
- `updatedAt`: Timestamp
- `completedAt`: Timestamp (optional)

**Status:** Draft — TBD detailed fields

**Ownership:** Job / Processing Layer

---

### InputDataset

**Purpose:** Defines the source data for processing.

**Input:**
- `datasetId`: Unique identifier
- `type`: IMAGE | IMAGE_COLLECTION
- `source`: GEE asset ID or collection path
- `filters`: Array of Filter definitions
- `bands`: Array of band names (optional)

**Output:**
- Validated dataset reference ready for GEE

**Status:** Draft — TBD detailed fields

**Ownership:** Job / Processing Layer → GEE Integration Layer

---

### Image / ImageCollection

**Purpose:** GEE data abstractions used in processing.

**Input:**
- GEE Image or ImageCollection object (internal to GEE Integration Layer)

**Output:**
- Processed Image or ImageCollection

**Status:** TBD — GEE-native types

**Ownership:** GEE Integration Layer

---

### AOI (Area of Interest)

**Purpose:** Geographic boundary for processing.

**Input:**
- `geometry`: GeoJSON geometry (Polygon, MultiPolygon, Point)
- `crs`: Coordinate reference system (default: EPSG:4326)
- `name`: Human-readable name (optional)

**Output:**
- Validated geometry for GEE operations

**Status:** Draft — TBD validation rules

**Ownership:** Application → Job Layer → GEE Integration Layer

---

### ProcessingOperation

**Purpose:** Single processing step to apply.

**Input:**
- `operationId`: Unique identifier
- `type`: Operation type (e.g., "NDVI", "CLASSIFICATION", "MOSAIC", "REDUCE")
- `parameters`: Operation-specific parameters
- `input`: Reference to previous operation output or InputDataset

**Output:**
- Intermediate result reference

**Status:** Draft — TBD operation types

**Ownership:** Job / Processing Layer → GEE Integration Layer

---

### ProcessingParameters

**Purpose:** Global parameters for the processing job.

**Input:**
- `scale`: Output resolution in meters
- `crs`: Output coordinate reference system
- `crsTransform`: Affine transform (optional)
- `format`: Output format (GeoTIFF, etc.)
- `maxPixels`: Maximum pixels to process
- `tileScale`: Tile scaling factor
- `extra`: Additional GEE-specific parameters

**Output:**
- Validated parameters for GEE export

**Status:** Draft — TBD defaults and validation

**Ownership:** Job / Processing Layer → GEE Integration Layer

---

### Task

**Purpose:** Unit of work submitted to GEE.

**Input:**
- `taskId`: Unique identifier
- `jobId`: Parent job reference
- `operation`: ProcessingOperation reference
- `exportConfig`: Export configuration (destination, format, etc.)
- `status`: TaskStatus

**Output:**
- `taskId`: Same identifier
- `geeTaskId`: GEE-assigned task ID
- `status`: TaskStatus
- `progress`: Progress percentage (0-100)
- `error`: Error details (if failed)
- `startedAt`: Timestamp
- `completedAt`: Timestamp (optional)

**Status:** Draft — TBD detailed fields

**Ownership:** GEE Integration Layer → Task Management

---

### TaskStatus

**Purpose:** Enumeration of possible task states.

**Values:**
- `READY` — Task created, not yet submitted
- `SUBMITTED` — Submitted to GEE, awaiting start
- `RUNNING` — Actively executing in GEE
- `COMPLETED` — Finished successfully
- `FAILED` — Execution failed
- `CANCELLED` — Cancelled by user or system
- `TIMED_OUT` — Exceeded maximum runtime

**Status:** Draft

**Ownership:** GEE Integration Layer / Task Management

---

### ProcessingResult

**Purpose:** Final output of a completed processing job.

**Input:**
- `jobId`: Parent job reference
- `assets`: Array of output asset references (GEE assets, Cloud Storage URIs, etc.)
- `metadata`: Processing metadata (stats, bounds, etc.)
- `format`: Output format

**Output:**
- Deliverable result for Application/User

**Status:** Draft — TBD asset types

**Ownership:** Result Management → Processing API → Application

---

### ProcessingError

**Purpose:** Standardized error representation.

**Input:**
- `code`: Error code (e.g., "GEE_AUTH_FAILED", "EXPORT_FAILED", "QUOTA_EXCEEDED")
- `message`: Human-readable description
- `details`: Structured error details
- `retryable`: Boolean indicating if retry may succeed
- `source`: Component where error originated

**Output:**
- Error information for logging, retry logic, and user display

**Status:** Draft — TBD error code taxonomy

**Ownership:** All layers (each defines errors for their domain)

---

## Contract Evolution

- Contracts are **versioned** — breaking changes require new version
- Architect owns contract definitions and approvals
- Coding Agent implements to contract specifications
- Changes require Architect review and Project Manager approval

---

## Status

All contracts are **Draft** status. They will be refined during Block 3 (Processing Job Model) and validated during implementation.