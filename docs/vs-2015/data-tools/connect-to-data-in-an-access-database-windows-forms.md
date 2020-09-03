---
title: Conectarse a datos en una base de datos de Access (Windows Forms) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 8426e9fcaa29bef36b6701c78d622f6f42fd1171
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "72651140"
---
# <a name="connect-to-data-in-an-access-database-windows-forms"></a>Conectar a los datos en una base de datos de Access (Windows Forms)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Puede conectarse a una base de datos de Access (ya sea un archivo. MDF o. accdb) mediante Visual Studio. Después de definir la conexión, los datos aparecen en la ventana **Orígenes de datos**. Desde esta ventana, puede arrastrar las tablas o vistas a los formularios.

## <a name="prerequisites"></a>Prerrequisitos
 Para usar estos procedimientos, necesita un proyecto de aplicación de Windows Forms y una base de datos de Access (archivo. accdb) o una base de datos de Access 2000 – 2003 (archivo. mdb). Siga el procedimiento que corresponde al tipo de archivo.

## <a name="creating-the-dataset-for-an-accdb-file"></a>Crear el conjunto de datos para un archivo .accdb
 Puede conectarse a las bases de datos creadas a través de Access 2013, Office 365, Access 2010 o Access 2007 mediante el procedimiento siguiente.

#### <a name="to-create-the-dataset"></a>Crear el conjunto de datos

1. Abra la aplicación de Windows Forms para la que desea crear una conexión de datos.

2. En el menú **Ver** , seleccione **otros**  >  **orígenes de datos**de Windows.

     ![Ver orígenes de datos en Otras ventanas](../data-tools/media/viewdatasources.png "ViewDataSources")

3. En la ventana **Orígenes de datos** , seleccione **Agregar nuevo origen de datos**.

     ![Agregar nuevo origen de datos](../data-tools/media/dataaddnewdatasource.png "dataAddNewDataSource")

4. Seleccione **base** de datos en la página **elegir un tipo de origen de datos** y, a continuación, seleccione **siguiente**.

5. Seleccione **conjunto** de datos en la página **elegir un modelo de base de datos** y, a continuación, seleccione **siguiente**.

6. En la página **Elegir la conexión de datos**, seleccione **Nueva conexión** para configurar una nueva conexión de datos.

7. Cambie el **origen de datos** a **.NET Framework proveedor de datos para OLE DB**.

     ![Cambiar proveedor de datos a OLE DB](../data-tools/media/datachangedatasourceoledb.png "dataChangeDataSourceOLEDB")

    > [!IMPORTANT]
    > Aunque el origen de datos de un archivo de base de datos de **Microsoft Access (OLE DB)** podría parecer la elección correcta, solo se usa ese tipo de origen de datos para los archivos de base de datos. mdb.

8. En **OLE DB proveedor**, seleccione **Microsoft Office motor de base de datos de acceso de OLE DB 12,0**.

     ![Proveedor OLE DB de Microsoft Office 12.0 Access](../data-tools/media/dataoledbprovideroffice12access.png "dataOLEDBProviderOffice12Access")

9. En **servidor o nombre de archivo**, especifique la ruta de acceso y el nombre del archivo. accdb al que desea conectarse y, a continuación, seleccione **Aceptar**.

    > [!NOTE]
    > Si el archivo de base de datos tiene un nombre de usuario y una contraseña, especifíquelo antes de seleccionar **Aceptar**.

10. Seleccione **siguiente** en la página **elegir la conexión de datos** .

11. Seleccione **siguiente** en la página **Guardar cadena de conexión en el archivo de configuración de la aplicación** .

12. Expanda el nodo **tablas** en la página **Elija los objetos de base de datos** .

13. Seleccione las tablas o vistas que desee en el conjunto de DataSet y, a continuación, seleccione **Finalizar**.

     El conjunto de datos se agrega al proyecto y las tablas y las vistas aparecen en la ventana **Orígenes de datos**.

## <a name="creating-the-dataset-for-an-mdb-file"></a>Crear el conjunto de información para un archivo. mdb
 Cree el conjunto de datos ejecutando el **Asistente para la configuración de orígenes de datos**.

#### <a name="to-create-the-dataset"></a>Crear el conjunto de datos

1. Abra la aplicación de Windows Forms para la que desea crear una conexión de datos.

2. En el menú **Ver** , seleccione **otros**  >  **orígenes de datos**de Windows.

     ![Ver orígenes de datos en Otras ventanas](../data-tools/media/viewdatasources.png "ViewDataSources")

3. En la ventana **Orígenes de datos** , seleccione **Agregar nuevo origen de datos**.

4. Seleccione **base** de datos en la página **elegir un tipo de origen de datos** y, a continuación, seleccione **siguiente**.

5. Seleccione **conjunto** de datos en la página **elegir un modelo de base de datos** y, a continuación, seleccione **siguiente**.

6. En la página **Elegir la conexión de datos**, seleccione **Nueva conexión** para configurar una nueva conexión de datos.

7. Si el origen de datos no es un archivo de base de datos de **Microsoft Access (OLE DB)**, seleccione **cambiar** para abrir el cuadro de diálogo **cambiar origen de datos** y seleccione Archivo de base de datos de **Microsoft Access**y, a continuación, seleccione **Aceptar**.

8. En el **nombre del archivo de base de datos**, especifique la ruta de acceso y el nombre del archivo. mdb al que desea conectarse y, a continuación, seleccione **Aceptar**.

     ![Agregar archivo de base de datos de acceso a la conexión](../data-tools/media/dataaddconnectionaccessmdb.png "dataAddConnectionAccessMDB")

9. Seleccione **siguiente** en la página **elegir la conexión de datos** .

10. Seleccione **siguiente** en la página **Guardar cadena de conexión en el archivo de configuración de la aplicación** .

11. Expanda el nodo **tablas** en la página **Elija los objetos de base de datos** .

12. Seleccione las tablas o vistas que desee en el conjunto de DataSet y, a continuación, seleccione **Finalizar**.

     El conjunto de datos se agrega al proyecto y las tablas y las vistas aparecen en la ventana **Orígenes de datos**.

## <a name="security"></a>Seguridad
 Almacenar información confidencial, como una contraseña, puede afectar la seguridad de la aplicación. El uso de la autenticación de Windows (también conocida como seguridad integrada) es un modo más seguro de controlar el acceso a una base de datos. Para más información, consulte [Proteger la información de conexión](https://msdn.microsoft.com/library/1471f580-bcd4-4046-bdaf-d2541ecda2f4).

## <a name="next-steps"></a>Pasos siguientes
 El conjunto de datos que acaba de crear ahora está disponible en la ventana **orígenes de datos** . Ahora puede realizar cualquiera de las tareas siguientes:

- Seleccione elementos en la ventana **orígenes de datos** y arrástrelos al formulario (vea [enlazar controles de Windows Forms a datos en Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)).

- Abra el origen de datos en el Diseñador de DataSet para agregar o editar los objetos que constituyen el conjunto de datos.

- Agregue la lógica de validación <xref:System.Data.DataTable.ColumnChanging> al <xref:System.Data.DataTable.RowChanging> evento o de las tablas de datos en el conjunto de datos (vea [Validate Data in](../data-tools/validate-data-in-datasets.md)datasets).

## <a name="see-also"></a>Consulte también

 [Preparar la aplicación para recibir](https://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad) [controles de enlace de datos a los datos en Visual Studio validación de los](../data-tools/bind-controls-to-data-in-visual-studio.md) [Validating Data](https://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e) [tutoriales de datos](https://msdn.microsoft.com/library/15a88fb8-3bee-4962-914d-7a1f8bd40ec4) de datos