---
title: "Tutorial: Usar un archivo de configuración para definir un origen de datos | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- configuration files [Visual Studio ALM], defining data sources
- unit tests, walkthrough
- data sources, defining with configuration files
ms.author: gewarren
manager: ghogen
ms.workload: multiple
author: gewarren
ms.openlocfilehash: 269efd6f66d6430b9fa533c2cfebb6bdf0f78e3d
ms.sourcegitcommit: 7ae502c5767a34dc35e760ff02032f4902c7c02b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/09/2018
---
# <a name="walkthrough-using-a-configuration-file-to-define-a-data-source"></a>Tutorial: Utilizar un archivo de configuración para definir un origen de datos
Este tutorial muestra cómo usar un origen de datos definido en un archivo app.config para pruebas unitarias. Aprenderá a crear un archivo app.config que define un origen de datos que se puede usar en la clase <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute>. En este tutorial se presentan las tareas siguientes:  
  
-   Creación de un archivo app.config.  
  
-   Definición de una sección de configuración personalizada.  
  
-   Definición de cadenas de conexión.  
  
-   Definición de orígenes de datos.  
  
-   Acceso a los orígenes de datos mediante la clase <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute>.  
  
## <a name="prerequisites"></a>Requisitos previos  
 Para completar este tutorial, necesitará:  
  
-   Visual Studio Enterprise  
  
-   Que Microsoft Access o Microsoft Excel proporcione datos para al menos uno de los métodos de prueba.  
  
-   Una solución de Visual Studio que contenga un proyecto de prueba.  
  
## <a name="create-the-appconfig-file"></a>Crear el archivo app.config  
  
#### <a name="to-add-an-appconfig-file-to-the-project"></a>Para agregar un archivo app.config al proyecto:  
  
1.  Si el proyecto de prueba ya incluye un archivo app.config, vaya a [Definir una sección de configuración personalizada](#DefineCustomConfigurationSection).  
  
2.  En el **Explorador de soluciones**, haga clic con el botón derecho en el proyecto de prueba, apunte a **Agregar** y haga clic en **Nuevo elemento**.  
  
     Se abrirá la ventana **Agregar nuevo elemento**.  
  
3.  Seleccione la plantilla **Archivo de configuración de aplicaciones** y haga clic en **Agregar**.  
  
##  <a name="DefineCustomConfigurationSection"></a> Definir una sección de configuración personalizada  
 Examine el archivo app.config. Debe contener al menos la declaración XML y un elemento raíz.  
  
#### <a name="to-add-the-custom-configuration-section-to-the-appconfig-file"></a>Para agregar la sección de configuración personalizada al archivo app.config  
  
1.  El elemento raíz de app.config debe ser el elemento `configuration`. Cree un elemento `configSections` en el elemento `configuration`. El elemento `configSections` debe ser el primero en el archivo app.config.  
  
2.  Dentro del elemento `configSections`, cree un elemento `section`.  
  
3.  En el elemento `section`, agregue un atributo denominado `name` y asígnele un valor igual a `microsoft.visualstudio.testtools`. Agregue otro atributo denominado `type` y asígnele un valor igual a `Microsoft.VisualStudio.TestTools.UnitTesting.TestConfigurationSection, Microsoft.VisualStudio.QualityTools.UnitTestFramework, Version=8.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a`.  
  
 El elemento `section` debe ser similar a este:  
  
```  
<section name="microsoft.visualstudio.testtools" type="Microsoft.VisualStudio.TestTools.UnitTesting.TestConfigurationSection, Microsoft.VisualStudio.QualityTools.UnitTestFramework, Version=8.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a"/>  
```  
  
> [!NOTE]
>  El nombre del ensamblado debe coincidir con la compilación de Microsoft Visual Studio .NET Framework que está usando. Establezca la versión en 9.0.0.0 si usa Visual Studio .NET Framework 3.5. Si usa Visual Studio .NET Framework 2.0, establezca la versión en 8.0.0.0.  
  
## <a name="define-connection-strings"></a>Definir cadenas de conexión  
 Las cadenas de conexión definen la información específica del proveedor para acceder a los orígenes de datos. Las cadenas de conexión definidas en los archivos de configuración proporcionan información del proveedor de datos reutilizable en una aplicación. En esta sección, creará dos cadenas de conexión para que las usen los orígenes de datos definidos en la sección de configuración personalizada.  
  
#### <a name="to-define-connection-strings"></a>Para definir cadenas de conexión:  
  
1.  Tras el elemento `configSections`, cree un elemento `connectionStrings`.  
  
2.  Dentro del elemento `connectionStrings`, cree dos elementos `add`.  
  
3.  En el primer elemento `add`, cree los atributos y los valores siguientes para una conexión con una base de datos de Microsoft Access:  
  
|Atributo|Valores|  
|---------------|------------|  
|`name`|`"MyJetConn"`|  
|`connectionString`|`"Provider=Microsoft.Jet.OLEDB.4.0; Data Source=C:\testdatasource.accdb; Persist Security Info=False;"`|  
|`providerName`|`"System.Data.OleDb"`|  
  
 En el segundo elemento `add`, cree los atributos y los valores siguientes para una conexión con una hoja de cálculo de Microsoft Excel:  
  
|||  
|-|-|  
|`name`|`"MyExcelConn"`|  
|`connectionString`|`"Dsn=Excel Files;dbq=data.xlsx;defaultdir=.; driverid=790;maxbuffersize=2048;pagetimeout=5"`|  
|`providerName`|`"System.Data.Odbc"`|  
  
 El elemento `connectionStrings` debe ser similar a este:  
  
```  
<connectionStrings>  
    <add name="MyJetConn" connectionString="Provider=Microsoft.Jet.OLEDB.4.0; Data Source=C:\testdatasource.accdb; Persist Security Info=False;" providerName="System.Data.OleDb" />  
    <add name="MyExcelConn" connectionString="Dsn=Excel Files;dbq=data.xlsx;defaultdir=.; driverid=790;maxbuffersize=2048;pagetimeout=5" providerName="System.Data.Odbc" />  
</connectionStrings>  
```  
  
## <a name="define-data-sources"></a>Definir orígenes de datos  
 La sección de orígenes de datos contiene cuatro atributos con los que el motor de pruebas recuperará los datos de un origen de datos.  
  
-   `name` define la identidad con la que <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute> especifica el origen de datos que se debe usar.  
  
-   `connectionString` identifica la cadena de conexión que ha creado en la sección Definir cadenas de conexión anterior.  
  
-   `dataTableName` define la tabla o la hoja que contiene los datos que se van a usar en la prueba.  
  
-   `dataAccessMethod` define la técnica para acceder a los valores de datos del origen de datos.  
  
 En esta sección, definirá dos orígenes de datos que se usarán en una prueba unitaria.  
  
#### <a name="to-define-data-sources"></a>Para definir orígenes de datos:  
  
1.  Tras el elemento `connectionStrings`, cree un elemento `microsoft.visualstudio.testtools`. El contenido de esta sección ya se ha creado en Definir una sección de configuración personalizada.  
  
2.  Dentro del elemento `microsoft.visualstudio.testtools`, cree un elemento `dataSources`.  
  
3.  Dentro del elemento `dataSources`, cree dos elementos `add`.  
  
4.  En el primer elemento `add`, cree los atributos y los valores siguientes para un origen de datos de Microsoft Access:  
  
|Atributo|Valores|  
|---------------|------------|  
|`name`|`"MyJetDataSource"`|  
|`connectionString`|`"MyJetConn"`|  
|`dataTableName`|`"MyDataTable"`|  
|`dataAccessMethod`|`"Sequential"`|  
  
 En el segundo elemento `add`, cree los atributos y los valores siguientes para un origen de datos de Microsoft Excel:  
  
|||  
|-|-|  
|`Name`|`"MyExcelDataSource"`|  
|`connectionString`|`"MyExcelConn"`|  
|`dataTableName`|`"Sheet1$"`|  
|`dataAccessMethod`|`"Sequential"`|  
  
 El elemento `microsoft.visualstudio.testtools` debe ser similar a este:  
  
```  
<microsoft.visualstudio.testtools>  
    <dataSources>  
        <add name="MyJetDataSource" connectionString="MyJetConn" dataTableName="MyDataTable" dataAccessMethod="Sequential"/>  
        <add name="MyExcelDataSource" connectionString="MyExcelConn" dataTableName="Sheet1$" dataAccessMethod="Sequential"/>  
    </dataSources>  
</microsoft.visualstudio.testtools>  
```  
  
 El archivo app.config final debe ser similar a este:  
  
```  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
    <configSections>  
        <section name="microsoft.visualstudio.testtools" type="Microsoft.VisualStudio.TestTools.UnitTesting.TestConfigurationSection, Microsoft.VisualStudio.QualityTools.UnitTestFramework, Version=8.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a"/>   
    </configSections>  
    <connectionStrings>  
        <add name="MyJetConn" connectionString="Provider=Microsoft.Jet.OLEDB.4.0; Data Source=C:\testdatasource.accdb; Persist Security Info=False;" providerName="System.Data.OleDb" />  
        <add name="MyExcelConn" connectionString="Dsn=Excel Files;dbq=data.xlsx;defaultdir=.; driverid=790;maxbuffersize=2048;pagetimeout=5" providerName="System.Data.Odbc" />  
    </connectionStrings>  
    <microsoft.visualstudio.testtools>  
        <dataSources>  
            <add name="MyJetDataSource" connectionString="MyJetConn" dataTableName="MyDataTable" dataAccessMethod="Sequential"/>  
            <add name="MyExcelDataSource" connectionString="MyExcelConn" dataTableName="Sheet1$" dataAccessMethod="Sequential"/>  
        </dataSources>  
    </microsoft.visualstudio.testtools>  
</configuration>  
```  
  
## <a name="create-a-unit-test-using-data-sources-defined-in-appconfig"></a>Crear una prueba unitaria con los orígenes de datos definidos en app.config  
 Una vez definido el archivo app.config, deberá crear una prueba unitaria que use los datos ubicados en los orígenes de datos definidos en dicho archivo. En esta sección:  
  
-   Creará los orígenes de datos que se encuentran en el archivo app.config.  
  
-   Usará los orígenes de datos en dos métodos de prueba que comparan los valores de cada uno de estos orígenes.  
  
#### <a name="to-create-a-microsoft-access-data-source"></a>Para crear un origen de datos de Microsoft Access:  
  
1.  Cree una base de datos de Microsoft Access denominada `testdatasource.accdb`.  
  
2.  Cree una tabla y asígnele el nombre de `MyDataTable` en `testdatasource.accdb`.  
  
3.  Cree dos campos en `MyDataTable` denominados `Arg1` y `Arg2` con el tipo de datos `Number`.  
  
4.  Agregue cinco entidades a `MyDataTable` con los valores siguientes para `Arg1` y `Arg2` respectivamente: (10,50), (3,2), (6,0), (0,8) y (12312,1000).  
  
5.  Guarde y cierre la base de datos.  
  
6.  Cambie la cadena de conexión para que apunte a la ubicación de la base de datos. Cambie el valor de `Data Source` para que refleje la ubicación de la base de datos.  
  
#### <a name="to-create-a-microsoft-excel-data-source"></a>Para crear un origen de datos de Microsoft Excel:  
  
1.  Cree una hoja de cálculo de Microsoft Excel denominada `data.xlsx`.  
  
2.  Cree una hoja denominada `Sheet1` si no existe en `data.xlsx`.  
  
3.  Cree dos encabezados de columna y asígneles los nombres de `Val1` y `Val2` en `Sheet1`.  
  
4.  Agregue cinco entidades a `Sheet1` con los valores siguientes para `Val1` y `Val2` respectivamente: (1,1), (2,2), (3,3), (4,4) y (5,0).  
  
5.  Guarde y cierre la hoja de cálculo.  
  
6.  Cambie la cadena de conexión para que apunte a la ubicación de la hoja de cálculo. Cambie el valor de `dbq` para que refleje la ubicación de la hoja de cálculo.  
  
#### <a name="to-create-a-unit-test-using-the-appconfig-data-sources"></a>Para crear una prueba unitaria con los orígenes de datos de app.config:  
  
1.  Agregue una prueba unitaria al proyecto de prueba.  
  
     Para más información, vea [Crear y ejecutar pruebas unitarias para código existente](http://msdn.microsoft.com/en-us/e8370b93-085b-41c9-8dec-655bd886f173).  
  
2.  Reemplace el contenido de la prueba unitaria generado automáticamente por el código siguiente:  
  
    ```  
    using System;  
    using Microsoft.VisualStudio.TestTools.UnitTesting;  
  
    namespace TestProject1  
    {  
         [TestClass]  
        public class UnitTest1  
        {  
            private TestContext context;  
  
            public TestContext TestContext  
            {  
                get { return context; }  
                set { context = value; }  
            }  
  
            [TestMethod()]  
            [DeploymentItem("MyTestProject\\testdatasource.accdb")]  
            [DataSource("MyJetDataSource")]  
            public void MyTestMethod()  
            {  
                int a = Int32.Parse(context.DataRow["Arg1"].ToString());  
                int b = Int32.Parse(context.DataRow["Arg2"].ToString());  
                Assert.AreNotEqual(a, b, "A value was equal.");  
            }  
  
            [TestMethod()]  
            [DeploymentItem("MyTestProject\\data.xlsx")]  
            [DataSource("MyExcelDataSource")]  
            public void MyTestMethod2()  
            {  
                Assert.AreEqual(context.DataRow["Val1"], context.DataRow["Val2"]);  
            }  
        }  
    }  
    ```  
  
3.  Examine los atributos DataSource. Observe los nombres de configuración del archivo app.config.  
  
4.  Compile la solución y ejecute las pruebas MyTestMethod y MyTestMethod2.  
  
> [!IMPORTANT]
>  Implemente los elementos como los orígenes de datos, para que la prueba pueda acceder a ellos en el directorio de implementación.  
  
## <a name="see-also"></a>Vea también

[Haga una prueba unitaria de su código](../test/unit-test-your-code.md)  
[Crear y ejecutar pruebas unitarias para código existente](http://msdn.microsoft.com/en-us/e8370b93-085b-41c9-8dec-655bd886f173)  
[Cómo: Crear una prueba unitaria controlada por datos](../test/how-to-create-a-data-driven-unit-test.md)
