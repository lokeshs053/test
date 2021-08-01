# test

```mermaid
classDiagram
  BaseSapBwObjectService <|-- InfoAreaService
  Consumer <|-- InfoAreaService
  BaseSapBwObjectService <|-- DataSourceService
  Consumer <|-- DataSourceService
  class Consumer {
    <<interface>>
    accept(InputParameter data)
  }
  class BaseSapBwObjectService {
    <<abstract>>
    #SapBwProperties appConfig
    #DbObjectSearchUtil searchUtil
	#SapBwDatabase database
    #BaseSapConfiguration sapBwConfiguration
    #JCoDestination jCoDestination
    #Map<String, String> tableConfigMap
    #String tableName
    #List<String> columnNames
    #String objectType
    #String delimiter = PIPE_SEPARATOR;
    #String primaryKey
    #DBUsageIndexer dbUsageIndexer
    +searchAndPopulateSapBwResponse()$ List~SapBwResponse~
    +invokeRFCMethodAndPopulateResponse()$ List~SapBwResponse~
    +invokeRFCMethodAndPopulateResponse()$ List~SapBwResponse~
    +searchSapBwResponseAndProcess()
    +extractAndIndexSapBwResponseObject()
	+searchAndPopulateSapBwResponse()
    +defaultConfig()
    +populateSapBwResponseWithDefaultValue()
    +configurePaginationSize()
    +populateMultiLanguage()
	+copyColumnsValue()
  }
  class InfoAreaService {
    -searchAndIndexInfoAreaText()
    -searchAndIndexInfoAreaReferenceCount()
    -populateReferenceCount()
    -populateInfoAreaText()$ SapBwResponseObject
  }
  class DataSourceService {
    -searchAndIndexDataSourceData()
    -searchAndIndexDataSourceExternalData()
    -searchAndIndexDataSourceText()
    -searchAndIndexDataSourceField()
    -searchAndIndexDataSourceFieldText()
	-populateDataSource()$ SapBwResponseObject
	-populateDataSourceTexts()$ SapBwResponseObject
	-populateDataSourceField()$ SapBwResponseObject
	-populateDataSourceFieldText()$ SapBwResponseObject
	-populateFieldData()
	-populateFieldTextData()
	-populateJsonData()
  }
  ```
