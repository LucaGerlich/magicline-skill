# Update a contract idle period

Required Scopes: 

Update a contract idle period. When the amendment is accepted, it will become an idle period. ATTENTION: Please see https://developer.magicline.com/apis/openapi/general-information#multipartform-data-requests

Endpoint: PUT /v1/memberships/{contractId}/self-service/idle-periods/{idlePeriodId}
Version: 1.11.0
Security: ApiKeyAuth

## Path parameters:

  - `contractId` (integer, required)
    Unique ID of the contract

  - `idlePeriodId` (integer, required)
    Unique ID of the idle period

## Request fields (multipart/form-data):

  - `data` (object, required)
    Represents an idle period update request

  - `data.startDate` (string, required)
    Start date of the idle period

  - `data.temporalUnit` (string)
    Represents the temporal unit of an idle period
    Enum: "DAY", "WEEK", "MONTH"

  - `data.termValue` (integer)
    Duration term of the idle period. The field is related to the temporal unit
    Example: 1

  - `data.unlimited` (boolean)
    If true, the idle period has no defined end date. In that case, termValue and temporalUnit are empty.
    Example: true

  - `data.reasonId` (integer, required)
    ID of an idle period reason
    Example: 1

  - `data.endDate` (string)
    End date of the idle period. This field is only utilized when shortening an existing idle period (i.e., the start date remains unchanged, but the new end date is earlier than the original).
    Example: "2025-12-31"

  - `document` (string)
    Idle period proposal document (jpeg, png, pdf, heic)

## Response 200 fields (application/json):

  - `id` (integer, required)
    Unique ID of the idle period or amendment, depending on the state
    Example: 203

  - `startDate` (string, required)
    Start date of the idle period

  - `endDate` (string, required)
    End date of the idle period

  - `unlimited` (boolean)
    Indicates whether the idle period is unlimited

  - `documentUrl` (string)
    Temporal download-url for the idle period document, restricted to 15 minutes

  - `state` (string, required)
    State of the idle period
    Enum: "PENDING_VERIFICATION", "ACCEPTED"

  - `idlePeriodFeeCalculationConfig` (object)
    Configuration for idle period fee calculation

  - `idlePeriodFeeCalculationConfig.idlePeriodAmount` (object, required)
    The idle period amount

  - `idlePeriodFeeCalculationConfig.idlePeriodAmount.amount` (number, required)
    Amount of the finance data tuple
    Example: 20

  - `idlePeriodFeeCalculationConfig.idlePeriodAmount.currency` (string, required)
    Currency of the finance data tuple
    Example: "EUR"

  - `idlePeriodFeeCalculationConfig.idlePeriodAmountPerTermUnit` (object)
    The idle period amount per term unit

  - `idlePeriodFeeCalculationConfig.defaultTemporalUnit` (string)
    The default temporal unit for the idle period
    Enum: "DAY", "WEEK", "MONTH"

  - `idlePeriodFeeCalculationConfig.dynamicIdlePeriodAmountPercentage` (number)
    The dynamic idle period amount percentage
    Example: 10

  - `idlePeriodFeeCalculationConfig.recurringIdlePeriodCharges` (boolean)
    Indicates whether recurring idle period charges are enabled

  - `idlePeriodFee` (object)
    Fee details for the idle period

  - `idlePeriodFee.idlePeriodFeeCalculationType` (string)
    The type of fee calculation used for the idle period
    Enum: "NONE", "ABSOLUTE", "RELATIVE", "TERM_BASED"

  - `idlePeriodFee.idlePeriodTotalAmount` (object)
    The total amount for the idle period

  - `idlePeriodFee.idlePeriodFeeCalculationAmount` (object)
    The amount used for fee calculation

  - `idlePeriodFee.idlePeriodFeeCalculationTerm` (object)
    The term used for fee calculation

  - `idlePeriodFee.idlePeriodFeeCalculationTerm.value` (integer, required)
    The value of the term
    Example: 2

  - `idlePeriodFee.idlePeriodFeeCalculationTerm.unit` (string, required)
    Represents a temporal unit
    Enum: "DAY", "WEEK", "MONTH", "YEAR"

  - `idlePeriodFee.idlePeriodFeeCalculationPercentage` (number)
    The percentage used for fee calculation
    Example: 10

  - `idlePeriodReason` (object, required)
    The idle period reason details

  - `idlePeriodReason.id` (integer, required)
    Unique ID of the idle period reason
    Example: 203

  - `idlePeriodReason.name` (string, required)
    Name of the idle period reason
    Example: "Vacation"

  - `idlePeriodReason.documentRequired` (boolean, required)
    Whether the idle period reason requires a document of proof

  - `reason` (string, required)
    Reason of the idle period
    Example: "Vacation"

  - `fee` (object, required)
    Represents a financial data

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

