---
title: Conectarse a datos en una base de datos de Access (Windows Forms) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- databases, connecting to
- databases, Access
- data [Visual Studio], connecting
- connecting to data, from Access databases
- Access databases, connecting
ms.assetid: 4159e815-d430-4ad0-a234-e4125fcbef18
caps.latest.revision: 32
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 4741dedb907bb88513147a98b916831abd965576
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49207355"
---
# <a name="connect-to-data-in-an-access-database-windows-forms"></a>Conectarse a datos en una base de datos de Access (Windows Forms)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Puede conectarse a una base de datos de Access (un archivo .mdf o un archivo .accdb) mediante el uso de Visual Studio. Después de definir la conexión, los datos aparecen en la **orígenes de datos** ventana. Desde esta ventana, puede arrastrar las tablas o vistas a los formularios. Si desea comprender cómo el sistema del proyecto en Visual Studio administra estos archivos de base de datos local, consulte [Cómo: administrar archivos de datos locales en el proyecto](../data-tools/how-to-manage-local-data-files-in-your-project.md).  
  
## <a name="prerequisites"></a>Requisitos previos  
 Para usar estos procedimientos, necesita un proyecto de aplicación Windows Forms y una base de datos de Access (archivo .accdb) o una base de datos de Access 2000 – 2003 (archivo .mdb). Siga el procedimiento que corresponde al tipo de archivo.  
  
## <a name="creating-the-dataset-for-an-accdb-file"></a>Crear el conjunto de datos para un archivo .accdb  
 Puede conectarse a bases de datos creadas a través de Access 2013, Office 365, Access 2010 o Access 2007 mediante el procedimiento siguiente.  
  
#### <a name="to-create-the-dataset"></a>Para crear el conjunto de datos  
  
1.  Abra la aplicación de Windows Forms a la que desea conectarse a datos.  
  
2.  En el **vista** menú, seleccione **Other Windows** > **orígenes de datos**.  
  
     ![Ver otros orígenes de datos de Windows](../data-tools/media/viewdatasources.png "ViewDataSources")  
  
3.  En la ventana **Orígenes de datos** , seleccione **Agregar nuevo origen de datos**.  
  
     ![Agregar nuevo origen de datos](../data-tools/media/dataaddnewdatasource.png "dataAddNewDataSource")  
  
4.  Seleccione **base de datos** en el **elegir un tipo de origen de datos** página y, a continuación, seleccione **siguiente**.  
  
5.  Seleccione **Dataset** en el **elegir un modelo de base de datos** página y, a continuación, seleccione **siguiente**.  
  
6.  En el **elegir la conexión de datos** página, seleccione **nueva conexión** para configurar una nueva conexión de datos.  
  
7.  Cambiar el **origen de datos** a **proveedor de datos de .NET Framework para OLE DB**.  
  
     ![Cambiar el proveedor de datos OLE DB](../data-tools/media/datachangedatasourceoledb.png "dataChangeDataSourceOLEDB")  
  
    > [!IMPORTANT]
    >  Aunque un origen de datos de **archivo de base de datos de Microsoft Access (OLE DB)** puede parecer la opción adecuada, usar ese tipo de origen de datos solo para archivos .mdb de base de datos.  
  
8.  En **proveedor OLE DB**, seleccione **Microsoft Office 12.0 Access Database Engine OLE DB Provider**.  
  
     ![Proveedor OLE DB Microsoft Office 12.0 Access](../data-tools/media/dataoledbprovideroffice12access.png "dataOLEDBProviderOffice12Access")  
  
9. En **nombre de archivo o servidor**, especifique la ruta de acceso y el nombre del archivo .accdb al que desea conectarse y, a continuación, seleccione **Aceptar**.  
  
    > [!NOTE]
    >  Si el archivo de base de datos tiene un nombre de usuario y una contraseña, especificar estos recursos antes de seleccionar **Aceptar**.  
  
10. Seleccione **siguiente** en el **elegir la conexión de datos** página.  
  
11. Seleccione **siguiente** en el **Guardar cadena de conexión en el archivo de configuración de la aplicación** página.  
  
12. Expanda el **tablas** nodo en el **elija los objetos de base de datos** página.  
  
13. Seleccione las tablas o vistas que desee en el conjunto de datos y, a continuación, seleccione **finalizar**.  
  
     El conjunto de datos se agrega al proyecto y las tablas y vistas aparecen en la **orígenes de datos** ventana.  
  
## <a name="creating-the-dataset-for-an-mdb-file"></a>Crear el conjunto de datos para un archivo .mdb  
 Crear el conjunto de datos mediante la ejecución de la **Asistente para configuración de origen de datos**.  
  
#### <a name="to-create-the-dataset"></a>Para crear el conjunto de datos  
  
1.  Abra la aplicación de Windows Forms a la que desea conectarse a datos.  
  
2.  En el **vista** menú, seleccione **Other Windows** > **orígenes de datos**.  
  
     ![Ver otros orígenes de datos de Windows](../data-tools/media/viewdatasources.png "ViewDataSources")  
  
3.  En la ventana **Orígenes de datos** , seleccione **Agregar nuevo origen de datos**.  
  
4.  Seleccione **base de datos** en el **elegir un tipo de origen de datos** página y, a continuación, seleccione **siguiente**.  
  
5.  Seleccione **Dataset** en el **elegir un modelo de base de datos** página y, a continuación, seleccione **siguiente**.  
  
6.  En el **elegir la conexión de datos** página, seleccione **nueva conexión** para configurar una nueva conexión de datos.  
  
7.  Si el origen de datos no es **archivo de base de datos de Microsoft Access (OLE DB)**, seleccione **cambio** para abrir el **cambiar origen de datos** cuadro de diálogo y seleccione **Microsoft Obtener acceso a archivos de base de datos**y, a continuación, seleccione **Aceptar**.  
  
8.  En el **nombre de archivo de base de datos**, especifique la ruta de acceso y el nombre del archivo .mdb en la que desea conectarse y, a continuación, seleccione **Aceptar**.  
  
     ![Agregar archivo de base de datos de acceso de conexión](../data-tools/media/dataaddconnectionaccessmdb.png "dataAddConnectionAccessMDB")  
  
9. Seleccione **siguiente** en el **elegir la conexión de datos** página.  
  
10. Seleccione **siguiente** en el **Guardar cadena de conexión en el archivo de configuración de la aplicación** página.  
  
11. Expanda el **tablas** nodo en el **elija los objetos de base de datos** página.  
  
12. Seleccione las tablas o vistas que desee en el conjunto de datos y, a continuación, seleccione **finalizar**.  
  
     El conjunto de datos se agrega al proyecto y las tablas y vistas aparecen en la **orígenes de datos** ventana.  
  
## <a name="security"></a>Seguridad  
 Almacenar información confidencial, como una contraseña, puede afectar la seguridad de la aplicación. El uso de la autenticación de Windows (también conocida como seguridad integrada) es un modo más seguro de controlar el acceso a una base de datos. Para más información, consulte [Proteger la información de conexión](http://msdn.microsoft.com/library/1471f580-bcd4-4046-bdaf-d2541ecda2f4).  
  
## <a name="next-steps"></a>Pasos siguientes  
 Ahora está disponible en el conjunto de datos que acaba de crear el **orígenes de datos** ventana. Ahora puede realizar cualquiera de las siguientes tareas:  
  
-   Seleccione los elementos en el **orígenes de datos** ventana y arrástrelos hasta el formulario (vea [controla el enlace Windows Forms a datos en Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)).  
  
-   Abra el origen de datos en el [Diseñador de Dataset](../data-tools/creating-and-editing-typed-datasets.md) para agregar o editar los objetos que componen el conjunto de datos.  
  
-   Agregar lógica de validación para el <xref:System.Data.DataTable.ColumnChanging> o <xref:System.Data.DataTable.RowChanging> eventos de las tablas de datos del conjunto de datos (consulte [validar datos en conjuntos de datos](../data-tools/validate-data-in-datasets.md)).  
  
## <a name="see-also"></a>Vea también  
 [Conectarse a datos en Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Preparar su aplicación para recibir datos](http://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad)   
 [Captura de datos en la aplicación](../data-tools/fetching-data-into-your-application.md)   
 [Enlazar controles a los datos en Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Edición de datos en la aplicación](../data-tools/editing-data-in-your-application.md)   
 [Validación de datos](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)   
 [Guardar datos](../data-tools/saving-data.md)   
 [Tutoriales de datos](http://msdn.microsoft.com/library/15a88fb8-3bee-4962-914d-7a1f8bd40ec4)

