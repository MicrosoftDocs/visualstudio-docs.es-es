---
title: Conectar a los datos en una base de datos de Access (Windows Forms)
ms.date: 02/12/2019
ms.topic: conceptual
helpviewer_keywords:
- databases, connecting to
- databases, Access
- data [Visual Studio], connecting
- connecting to data, from Access databases
- Access databases, connecting
ms.assetid: 4159e815-d430-4ad0-a234-e4125fcbef18
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 9d4fcce4664483cd1d981f6a0b1233a6302c553b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62568539"
---
# <a name="connect-to-data-in-an-access-database-windows-forms"></a>Conectar a los datos en una base de datos de Access (Windows Forms)

Puede conectarse a una base de datos de Access (ya sea un *.mdf* archivo o una *.accdb* archivo) mediante el uso de Visual Studio. Después de definir la conexión, los datos aparecen en la ventana **Orígenes de datos**. Desde esta ventana, puede arrastrar las tablas o vistas a los formularios.

## <a name="prerequisites"></a>Requisitos previos

Para utilizar estos procedimientos, se necesita un proyecto de aplicación de Windows Forms, y una base de datos de Access (archivo *.accdb*) o una base de datos de Access 2000-2003 (archivo *.mdb*). Siga el procedimiento que corresponde al tipo de archivo.

## <a name="create-a-dataset-for-an-accdb-file"></a>Crear un conjunto de datos para un archivo .accdb

Puede conectarse a bases de datos creadas a través de Access 2013, Office 365, Access 2010 o Access 2007 mediante el procedimiento siguiente.

1. Abra la aplicación de Windows Forms para la que desea crear una conexión de datos.

2. Para abrir el **orígenes de datos** ventana, en el **vista** menú, seleccione **Other Windows** > **orígenes de datos**.

   ![Ver orígenes de datos en Otras ventanas](../data-tools/media/viewdatasources.png)

3. En la ventana **Orígenes de datos** , seleccione **Agregar nuevo origen de datos**.

   Se abrirá el **Asistente para configuración de orígenes de datos**.

4. Seleccione **base de datos** en el **elegir un tipo de origen de datos** página y, a continuación, seleccione **siguiente**.

5. Seleccione **Dataset** en el **elegir un modelo de base de datos** página y, a continuación, seleccione **siguiente**.

6. En la página **Elegir la conexión de datos**, seleccione **Nueva conexión** para configurar una nueva conexión de datos.

   Se abrirá el cuadro de diálogo **Agregar conexión**.

7. Si **origen de datos** no está establecido en **archivo de base de datos de Microsoft Access (OLE DB)**, seleccione el **cambio** botón.

   El **cambiar origen de datos** abre el cuadro de diálogo. En la lista de orígenes de datos, elija **el archivo de base de datos de Microsoft Access**. En el **proveedor de datos** lista desplegable, seleccione **proveedor de datos de .NET Framework para OLE DB**y, a continuación, elija **Aceptar**.

8. Elija **examinar** junto a **nombre de archivo de base de datos**y, a continuación, navegue hasta su *.accdb* de archivo y elija **abierto**.

9. Escriba un nombre de usuario y una contraseña (si es necesario) y, a continuación, elija **Aceptar**.

10. Seleccione **siguiente** en el **elegir la conexión de datos** página.

     Obtendrá un cuadro de diálogo que le indica que el archivo de datos no está en el proyecto actual. Seleccione **Sí** o **No**.

11. Seleccione **siguiente** en el **Guardar cadena de conexión en el archivo de configuración de la aplicación** página.

12. Expanda el nodo **Tablas** en la página **Elija los objetos de base de datos**.

13. Seleccione las tablas o vistas que desea incluir en el conjunto de datos y, a continuación, seleccione **finalizar**.

     El conjunto de datos se agrega al proyecto y las tablas y las vistas aparecen en la ventana **Orígenes de datos**.

## <a name="create-a-dataset-for-an-mdb-file"></a>Crear un conjunto de datos para un archivo .mdb

Cree el conjunto de datos ejecutando el **Asistente para la configuración de orígenes de datos**.

1. Abra la aplicación de Windows Forms para la que desea crear una conexión de datos.

2. En el **vista** menú, seleccione **Other Windows** > **orígenes de datos**.

   ![Ver orígenes de datos en Otras ventanas](../data-tools/media/viewdatasources.png)

3. En la ventana **Orígenes de datos** , seleccione **Agregar nuevo origen de datos**.

    Se abrirá el **Asistente para configuración de orígenes de datos**.

4. Seleccione **base de datos** en el **elegir un tipo de origen de datos** página y, a continuación, seleccione **siguiente**.

5. Seleccione **Dataset** en el **elegir un modelo de base de datos** página y, a continuación, seleccione **siguiente**.

6. En la página **Elegir la conexión de datos**, seleccione **Nueva conexión** para configurar una nueva conexión de datos.

7. Si el origen de datos no es **archivo de base de datos de Microsoft Access (OLE DB)**, seleccione **cambio** para abrir el **cambiar origen de datos** cuadro de diálogo y seleccione **Microsoft Obtener acceso a archivos de base de datos**y, a continuación, seleccione **Aceptar**.

8. En el **nombre de archivo de base de datos**, especifique la ruta de acceso y el nombre de la *.mdb* archivo que desea conectarse a y, a continuación, seleccione **Aceptar**.

   ![Agregar archivo de base de datos de acceso a la conexión](../data-tools/media/add-connection-access-db.png)

9. Seleccione **siguiente** en el **elegir la conexión de datos** página.

10. Seleccione **siguiente** en el **Guardar cadena de conexión en el archivo de configuración de la aplicación** página.

11. Expanda el nodo **Tablas** en la página **Elija los objetos de base de datos**.

12. Seleccione las tablas o vistas que desee en el conjunto de datos y, a continuación, seleccione **finalizar**.

    El conjunto de datos se agrega al proyecto y las tablas y las vistas aparecen en la ventana **Orígenes de datos**.

## <a name="security"></a>Seguridad

Almacenar información confidencial, como una contraseña, puede afectar la seguridad de la aplicación. El uso de la autenticación de Windows (también conocida como seguridad integrada) es un modo más seguro de controlar el acceso a una base de datos. Para más información, consulte [Proteger la información de conexión](/dotnet/framework/data/adonet/protecting-connection-information).

## <a name="next-steps"></a>Pasos siguientes

Ahora está disponible en el conjunto de datos que acaba de crear el **orígenes de datos** ventana. Ahora puede realizar cualquiera de las tareas siguientes:

- Seleccione los elementos en el **orígenes de datos** ventana y arrástrelos hasta el formulario (vea [controla el enlace Windows Forms a datos en Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)).

- Abra el origen de datos en el **Diseñador de DataSet** para agregar o editar los objetos que constituyen el conjunto de datos.

- Agregar lógica de validación para el <xref:System.Data.DataTable.ColumnChanging> o <xref:System.Data.DataTable.RowChanging> eventos de las tablas de datos del conjunto de datos (consulte [validar datos en conjuntos de datos](../data-tools/validate-data-in-datasets.md)).

## <a name="see-also"></a>Vea también

- [Adición de conexiones](../data-tools/add-new-connections.md)