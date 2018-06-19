---
title: 'Cómo: Guardar y editar cadenas de conexión'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: f8ef3a2c-029c-423b-9d9e-a4f1add4f640
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: a1c0a7bc0659ecee5a65ca254f16eaa2d747ca76
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
ms.locfileid: "31916909"
---
# <a name="how-to-save-and-edit-connection-strings"></a>Cómo: Guardar y editar cadenas de conexión
Cadenas de conexión en aplicaciones de Visual Studio pueden guardar en el archivo de configuración de aplicación (conocido también como configuración de la aplicación) o codificado de forma rígida directamente en la aplicación. Si guarda las cadenas de conexión en el archivo de configuración de la aplicación, se simplifica la tarea de mantenimiento de la aplicación. Si la cadena de conexión debe modificarse, se puede actualizar en el archivo de configuración de la aplicación (cosa que no sucede si hubiera que cambiarla en el código fuente y tener que recompilar la aplicación).

Almacenar información confidencial (como la contraseña) en la cadena de conexión puede afectar la seguridad de la aplicación. Las cadenas de conexión almacenadas en el archivo de configuración de la aplicación no están ni cifradas ni protegidas, con lo cual existe la posibilidad de que alguien acceda al archivo y vea el contenido. El uso de la seguridad integrada de Windows es una forma más segura de controlar el acceso a una base de datos.

Si decide no usar la seguridad integrada de Windows y su base de datos requiere un nombre de usuario y una contraseña, estos se pueden omitir en la cadena de conexión, pero la aplicación tendrá que suministrar esta información para poder conectarse a la base de datos. Así, por ejemplo, puede crear un cuadro de diálogo que pida esta información al usuario y que cree la cadena de conexión dinámicamente en tiempo de ejecución. La seguridad puede seguir siendo un problema si alguien intercepta esa información en su recorrido a la base de datos.
Para más información, consulte [Proteger la información de conexión](/dotnet/framework/data/adonet/protecting-connection-information).

## <a name="to-save-a-connection-string-from-within-the-data-source-configuration-wizard"></a>Para guardar una cadena de conexión desde el Asistente para configuración de orígenes de datos
En el **Asistente para configuración de orígenes de datos**, seleccione la opción para guardar la conexión en Guardar la cadena de conexión a la página de archivo de configuración de aplicación.

## <a name="to-save-a-connection-string-directly-into-application-settings"></a>Para guardar la cadena de conexión directamente en la configuración de la aplicación
- En el Explorador de soluciones, haga doble clic en el icono de mi proyecto (Visual Basic) o el icono de propiedades (C#) para abrir el Diseñador de proyectos.
- Seleccione la pestaña Configuración.
- Escriba un nombre para la cadena de conexión. Haga referencia a este nombre cuando acceda a la cadena de conexión en el código.
- Establecer el tipo a (cadena de conexión).
- Deje el ámbito establecido en la aplicación.
- Escriba la cadena de conexión en el campo de valor o haga clic en el botón de puntos suspensivos (...) en el campo de valor para abrir el cuadro de diálogo Propiedades de conexión para generar la cadena de conexión.

## <a name="editing-connection-strings-stored-in-application-settings"></a>Modificar cadenas de conexión almacenadas en la configuración de aplicación
Puede modificar la información de conexión que se guarda en la configuración de la aplicación usando el Diseñador de proyectos.

### <a name="to-edit-a-connection-string-stored-in-application-settings"></a>Para modificar una cadena de conexión almacenada en la configuración de la aplicación
- En el Explorador de soluciones, haga doble clic en el icono de mi proyecto (Visual Basic) o el icono de propiedades (C#) para abrir el Diseñador de proyectos.
- Seleccione la pestaña Configuración.
- Busque la conexión que desea editar y seleccione el texto en el campo de valor.
- Modifique la cadena de conexión en el campo de valor o haga clic en el botón de puntos suspensivos (...) en el campo de valor para modificar la conexión con el cuadro de diálogo Propiedades de conexión.

## <a name="editing-connection-strings-for-datasets"></a>Modificar cadenas de conexión para los conjuntos de datos
Puede modificar la información de conexión para cada TableAdapter en un conjunto de datos.

### <a name="to-edit-a-connection-string-for-a-tableadapter-in-a-dataset"></a>Para editar una cadena de conexión para un TableAdapter en un conjunto de datos
- En el Explorador de soluciones, haga doble clic en el conjunto de datos (archivo .xsd) que tenga la conexión que desea editar.
- Seleccione el TableAdapter o consulta que tenga la conexión que desea editar.
- En la ventana Propiedades, expanda el nodo de conexión.
- Para modificar rápidamente la cadena de conexión, modifique la propiedad ConnectionString, o haga clic en la flecha hacia abajo en la propiedad de conexión y elija la nueva conexión.

## <a name="security"></a>Seguridad
Almacenar información confidencial (como una contraseña) en la cadena de conexión puede afectar la seguridad de la aplicación. El uso de la seguridad integrada de Windows es una forma más segura de controlar el acceso a una base de datos.
Para más información, consulte [Proteger la información de conexión](/dotnet/framework/data/adonet/protecting-connection-information).

## <a name="see-also"></a>Vea también

- [Adición de conexiones](../data-tools/add-new-connections.md)