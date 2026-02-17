# Get preview of an updated idle period charges and fees

Required Scopes: 

Get preview of an updated idle period charges and fees

Endpoint: PUT /v1/memberships/{contractId}/self-service/idle-periods/{idlePeriodId}/preview
Version: 1.11.0
Security: ApiKeyAuth

## Path parameters:

  - `contractId` (integer, required)
    Unique ID of the contract

  - `idlePeriodId` (integer, required)
    Unique ID of the idle period

## Request fields (application/json):

  - `startDate` (string, required)
    Start date of the idle period

  - `temporalUnit` (string)
    Represents the temporal unit of an idle period
    Enum: "DAY", "WEEK", "MONTH"

  - `termValue` (integer)
    Duration term of the idle period. The field is related to the temporal unit
    Example: 1

  - `unlimited` (boolean)
    If true, the idle period has no defined end date. In that case, termValue and temporalUnit are empty.
    Example: true

  - `reasonId` (integer, required)
    ID of an idle period reason
    Example: 1

  - `endDate` (string)
    End date of the idle period. This field is only utilized when shortening an existing idle period (i.e., the start date remains unchanged, but the new end date is earlier than the original).
    Example: "2025-12-31"

## Response 200 fields (application/json):

  - `previewEndDate` (string)
    Represents the updated contract end date
    Example: "2025-12-31"

  - `previewCharges` (array)
    The contract charges applicable following the idle period update

  - `previewCharges.paidPeriodFrom` (string)
    Start date of the paid period
    Example: "2025-01-01"

  - `previewCharges.paidPeriodTo` (string)
    End date of the paid period
    Example: "2025-01-31"

  - `previewCharges.dueDate` (string, required)
    Date to charge is/was to be paid
    Example: "2025-01-14"

  - `previewCharges.description` (string)
    Description of the charge

  - `previewCharges.amount` (object, required)
    Amount of the charge

  - `previewCharges.amount.amount` (number, required)
    Amount of the finance data tuple
    Example: 20

  - `previewCharges.amount.currency` (string, required)
    Currency of the finance data tuple
    Example: "EUR"

  - `previewCharges.discountedAmount` (object)
    Discounted amount of the charge

  - `validationStatus` (string, required)
    Status of the idle period validation
    Enum: "IDLEPERIOD_DEACTIVATED_FOR_CONTRACT", "IDLEPERIOD_PENDING_VERIFICATION", "IDLEPERIOD_DATE_NOT_FIRSTDAY_OF_TEMPORALUNIT", "IDLEPERIOD_DEADLINE_VIOLATED", "IDLEPERIOD_EXPECTED_STARTDATE_MISMATCH", "IDLEPERIOD_MAXIMUM_YEARS_VIOLATED", "IDLEPERIOD_OVERLAPPING", "IDLEPERIOD_TEMPORALUNIT_INVALID", "IDLEPERIOD_MAXIMUM_TERMS_VIOLATED", "IDLEPERIOD_CREATABLE", "IDLEPERIOD_TERMVALUE_MISSING", "IDLEPERIOD_UNLIMITED_PARAMETER_IS_MISSING", "IDLEPERIOD_ENDDATE_AND_TERM_PROVIDED", "IDLEPERIOD_ENDDATE_BEFORE_STARTDATE", "IDLEPERIOD_ENDDATE_ONLY_FOR_SHORTENING", "IDLEPERIOD_UPDATABLE"

## Response 400 fields (application/json):

  - `errorMessage` (string, required)
    Resolved message in the context-specific default locale

  - `errorCode` (string)
    Key for translation files

  - `traceId` (string)
    Datadog trace id

  - `reference` (string)
    Reference to validation error
    Example: "parent.child"

  - `args` (array)
    Arguments referenced by format specifiers while resolving the message from translation files

  - `typedArgs` (array)
    Same as  but with type information

  - `typedArgs.value` (object)

  - `typedArgs.type` (string)
    Enum: "TIMESTAMP", "BOOLEAN", "DATE", "MONTH_DAY", "TIME", "TERM", "TERM_LIST", "INTEGER", "DECIMAL", "STRING", "MONEY", "LIMITABLE_CONFIG_PROPERTY", "I18N_KEY", "I18N_KEY_LIST", "PERMISSION_LIST", "ENUM", "AVAILABILITY_LIST"

## Response 401 fields (application/json):

  - `errorMessage` (string, required)
    Resolved message in the context-specific default locale

  - `errorCode` (string)
    Key for translation files

  - `traceId` (string)
    Datadog trace id

  - `reference` (string)
    Reference to validation error
    Example: "parent.child"

  - `args` (array)
    Arguments referenced by format specifiers while resolving the message from translation files

  - `typedArgs` (array)
    Same as  but with type information

  - `typedArgs.value` (object)

  - `typedArgs.type` (string)
    Enum: "TIMESTAMP", "BOOLEAN", "DATE", "MONTH_DAY", "TIME", "TERM", "TERM_LIST", "INTEGER", "DECIMAL", "STRING", "MONEY", "LIMITABLE_CONFIG_PROPERTY", "I18N_KEY", "I18N_KEY_LIST", "PERMISSION_LIST", "ENUM", "AVAILABILITY_LIST"

## Response 403 fields (application/json):

  - `errorMessage` (string, required)
    Resolved message in the context-specific default locale

  - `errorCode` (string)
    Key for translation files

  - `traceId` (string)
    Datadog trace id

  - `reference` (string)
    Reference to validation error
    Example: "parent.child"

  - `args` (array)
    Arguments referenced by format specifiers while resolving the message from translation files

  - `typedArgs` (array)
    Same as  but with type information

  - `typedArgs.value` (object)

  - `typedArgs.type` (string)
    Enum: "TIMESTAMP", "BOOLEAN", "DATE", "MONTH_DAY", "TIME", "TERM", "TERM_LIST", "INTEGER", "DECIMAL", "STRING", "MONEY", "LIMITABLE_CONFIG_PROPERTY", "I18N_KEY", "I18N_KEY_LIST", "PERMISSION_LIST", "ENUM", "AVAILABILITY_LIST"

## Response 404 fields (application/json):

  - `errorMessage` (string, required)
    Resolved message in the context-specific default locale

  - `errorCode` (string)
    Key for translation files

  - `traceId` (string)
    Datadog trace id

  - `reference` (string)
    Reference to validation error
    Example: "parent.child"

  - `args` (array)
    Arguments referenced by format specifiers while resolving the message from translation files

  - `typedArgs` (array)
    Same as  but with type information

  - `typedArgs.value` (object)

  - `typedArgs.type` (string)
    Enum: "TIMESTAMP", "BOOLEAN", "DATE", "MONTH_DAY", "TIME", "TERM", "TERM_LIST", "INTEGER", "DECIMAL", "STRING", "MONEY", "LIMITABLE_CONFIG_PROPERTY", "I18N_KEY", "I18N_KEY_LIST", "PERMISSION_LIST", "ENUM", "AVAILABILITY_LIST"

## Response 409 fields (application/json):

  - `errorMessage` (string, required)
    Resolved message in the context-specific default locale

  - `errorCode` (string)
    Key for translation files

  - `traceId` (string)
    Datadog trace id

  - `reference` (string)
    Reference to validation error
    Example: "parent.child"

  - `args` (array)
    Arguments referenced by format specifiers while resolving the message from translation files

  - `typedArgs` (array)
    Same as  but with type information

  - `typedArgs.value` (object)

  - `typedArgs.type` (string)
    Enum: "TIMESTAMP", "BOOLEAN", "DATE", "MONTH_DAY", "TIME", "TERM", "TERM_LIST", "INTEGER", "DECIMAL", "STRING", "MONEY", "LIMITABLE_CONFIG_PROPERTY", "I18N_KEY", "I18N_KEY_LIST", "PERMISSION_LIST", "ENUM", "AVAILABILITY_LIST"

## Response 429 fields (application/json):

  - `errorMessage` (string, required)
    Resolved message in the context-specific default locale

  - `errorCode` (string)
    Key for translation files

  - `traceId` (string)
    Datadog trace id

  - `reference` (string)
    Reference to validation error
    Example: "parent.child"

  - `args` (array)
    Arguments referenced by format specifiers while resolving the message from translation files

  - `typedArgs` (array)
    Same as  but with type information

  - `typedArgs.value` (object)

  - `typedArgs.type` (string)
    Enum: "TIMESTAMP", "BOOLEAN", "DATE", "MONTH_DAY", "TIME", "TERM", "TERM_LIST", "INTEGER", "DECIMAL", "STRING", "MONEY", "LIMITABLE_CONFIG_PROPERTY", "I18N_KEY", "I18N_KEY_LIST", "PERMISSION_LIST", "ENUM", "AVAILABILITY_LIST"

## Response 500 fields (application/json):

  - `errorMessage` (string, required)
    Resolved message in the context-specific default locale

  - `errorCode` (string)
    Key for translation files

  - `traceId` (string)
    Datadog trace id

  - `reference` (string)
    Reference to validation error
    Example: "parent.child"

  - `args` (array)
    Arguments referenced by format specifiers while resolving the message from translation files

  - `typedArgs` (array)
    Same as  but with type information

  - `typedArgs.value` (object)

  - `typedArgs.type` (string)
    Enum: "TIMESTAMP", "BOOLEAN", "DATE", "MONTH_DAY", "TIME", "TERM", "TERM_LIST", "INTEGER", "DECIMAL", "STRING", "MONEY", "LIMITABLE_CONFIG_PROPERTY", "I18N_KEY", "I18N_KEY_LIST", "PERMISSION_LIST", "ENUM", "AVAILABILITY_LIST"

