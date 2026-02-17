# Get the idle periods of the contract

Required Scopes: 

Get contract idle periods. Amendments are returned, when a idle period is in status pending verification

Endpoint: GET /v1/memberships/{contractId}/self-service/idle-periods
Version: 1.11.0
Security: ApiKeyAuth

## Path parameters:

  - `contractId` (integer, required)
    Unique ID of the contract

## Response 200 fields (application/json):

  - `pastIdlePeriods` (array, required)
    Past idle period list

  - `pastIdlePeriods.id` (integer, required)
    Unique ID of the idle period or amendment, depending on the state
    Example: 203

  - `pastIdlePeriods.startDate` (string, required)
    Start date of the idle period

  - `pastIdlePeriods.endDate` (string, required)
    End date of the idle period

  - `pastIdlePeriods.unlimited` (boolean)
    Indicates whether the idle period is unlimited

  - `pastIdlePeriods.documentUrl` (string)
    Temporal download-url for the idle period document, restricted to 15 minutes

  - `pastIdlePeriods.state` (string, required)
    State of the idle period
    Enum: "PENDING_VERIFICATION", "ACCEPTED"

  - `pastIdlePeriods.idlePeriodFeeCalculationConfig` (object)
    Configuration for idle period fee calculation

  - `pastIdlePeriods.idlePeriodFeeCalculationConfig.idlePeriodAmount` (object, required)
    The idle period amount

  - `pastIdlePeriods.idlePeriodFeeCalculationConfig.idlePeriodAmount.amount` (number, required)
    Amount of the finance data tuple
    Example: 20

  - `pastIdlePeriods.idlePeriodFeeCalculationConfig.idlePeriodAmount.currency` (string, required)
    Currency of the finance data tuple
    Example: "EUR"

  - `pastIdlePeriods.idlePeriodFeeCalculationConfig.idlePeriodAmountPerTermUnit` (object)
    The idle period amount per term unit

  - `pastIdlePeriods.idlePeriodFeeCalculationConfig.defaultTemporalUnit` (string)
    The default temporal unit for the idle period
    Enum: "DAY", "WEEK", "MONTH"

  - `pastIdlePeriods.idlePeriodFeeCalculationConfig.dynamicIdlePeriodAmountPercentage` (number)
    The dynamic idle period amount percentage
    Example: 10

  - `pastIdlePeriods.idlePeriodFeeCalculationConfig.recurringIdlePeriodCharges` (boolean)
    Indicates whether recurring idle period charges are enabled

  - `pastIdlePeriods.idlePeriodFee` (object)
    Fee details for the idle period

  - `pastIdlePeriods.idlePeriodFee.idlePeriodFeeCalculationType` (string)
    The type of fee calculation used for the idle period
    Enum: "NONE", "ABSOLUTE", "RELATIVE", "TERM_BASED"

  - `pastIdlePeriods.idlePeriodFee.idlePeriodTotalAmount` (object)
    The total amount for the idle period

  - `pastIdlePeriods.idlePeriodFee.idlePeriodFeeCalculationAmount` (object)
    The amount used for fee calculation

  - `pastIdlePeriods.idlePeriodFee.idlePeriodFeeCalculationTerm` (object)
    The term used for fee calculation

  - `pastIdlePeriods.idlePeriodFee.idlePeriodFeeCalculationTerm.value` (integer, required)
    The value of the term
    Example: 2

  - `pastIdlePeriods.idlePeriodFee.idlePeriodFeeCalculationTerm.unit` (string, required)
    Represents a temporal unit
    Enum: "DAY", "WEEK", "MONTH", "YEAR"

  - `pastIdlePeriods.idlePeriodFee.idlePeriodFeeCalculationPercentage` (number)
    The percentage used for fee calculation
    Example: 10

  - `pastIdlePeriods.idlePeriodReason` (object, required)
    The idle period reason details

  - `pastIdlePeriods.idlePeriodReason.id` (integer, required)
    Unique ID of the idle period reason
    Example: 203

  - `pastIdlePeriods.idlePeriodReason.name` (string, required)
    Name of the idle period reason
    Example: "Vacation"

  - `pastIdlePeriods.idlePeriodReason.documentRequired` (boolean, required)
    Whether the idle period reason requires a document of proof

  - `pastIdlePeriods.reason` (string, required)
    Reason of the idle period
    Example: "Vacation"

  - `pastIdlePeriods.fee` (object, required)
    Represents a financial data

  - `currentAndUpcomingIdlePeriods` (array, required)
    Current and upcoming idle period list

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

