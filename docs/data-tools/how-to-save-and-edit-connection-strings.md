---
title: 'Cómo: Guardar y editar cadenas de conexión'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: f8ef3a2c-029c-423b-9d9e-a4f1add4f640
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: ed0f0105383667e1122d6636a3baab3aa925a742
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/01/2020
ms.locfileid: "75586463"
---
# <a name="how-to-save-and-edit-connection-strings"></a>Procedimiento para guardar y editar cadenas de conexión
Las cadenas de conexión de las aplicaciones de Visual Studio se guardan en el archivo de configuración de la aplicación (también conocido como configuración de la aplicación) o se codifican de forma rígida directamente en la aplicación. Si guarda las cadenas de conexión en el archivo de configuración de la aplicación, se simplifica la tarea de mantenimiento de la aplicación. Si la cadena de conexión debe modificarse, se puede actualizar en el archivo de configuración de la aplicación (cosa que no sucede si hubiera que cambiarla en el código fuente y tener que recompilar la aplicación).

Almacenar información confidencial (como la contraseña) en la cadena de conexión puede afectar la seguridad de la aplicación. Las cadenas de conexión almacenadas en el archivo de configuración de la aplicación no están ni cifradas ni protegidas, con lo cual existe la posibilidad de que alguien acceda al archivo y vea el contenido. El uso de la seguridad integrada de Windows es una forma más segura de controlar el acceso a una base de datos.

Si decide no usar la seguridad integrada de Windows y su base de datos requiere un nombre de usuario y una contraseña, estos se pueden omitir en la cadena de conexión, pero la aplicación tendrá que suministrar esta información para poder conectarse a la base de datos. Así, por ejemplo, puede crear un cuadro de diálogo que pida esta información al usuario y que cree la cadena de conexión dinámicamente en tiempo de ejecución. La seguridad puede seguir siendo un problema si alguien intercepta esa información en su recorrido a la base de datos.
Para más información, consulte [Proteger la información de conexión](/dotnet/framework/data/adonet/protecting-connection-information).

## <a name="to-save-a-connection-string-from-within-the-data-source-configuration-wizard"></a>Para guardar una cadena de conexión desde el Asistente para la configuración de orígenes de datos
En el **Asistente**para la configuración de orígenes de datos, seleccione la opción para guardar la conexión en la página **guardar la cadena de conexión en el archivo de configuración de la aplicación** .

## <a name="to-save-a-connection-string-directly-into-application-settings"></a>Para guardar la cadena de conexión directamente en la configuración de la aplicación
1. En el **Explorador de soluciones**, haga doble clic en el icono **Mi proyecto** (Visual Basic) o en el icono **Propiedades** (C#) para abrir el **Diseñador de proyectos**.
1. Seleccione la pestaña **Configuración**.
1. Escriba un **Nombre** para la cadena de conexión. Haga referencia a este nombre cuando acceda a la cadena de conexión en el código.
1. Establezca el **Tipo** en (**Cadena de conexión**).
1. Deje el **Ámbito** establecido en **Aplicación**.
1. Escriba la cadena de conexión en el campo **valor** o haga clic en el botón de **puntos suspensivos** (...) del campo **valor** para abrir el cuadro de diálogo **propiedades de conexión** para crear la cadena de conexión.

## <a name="edit-connection-strings-stored-in-application-settings"></a>Editar las cadenas de conexión almacenadas en la configuración de la aplicación
La información de conexión almacenada en la configuración de la aplicación se puede modificar con el **Diseñador de proyectos**.

### <a name="to-edit-a-connection-string-stored-in-application-settings"></a>Para modificar una cadena de conexión almacenada en la configuración de la aplicación
1. En el **Explorador de soluciones**, haga doble clic en el icono **Mi proyecto** (Visual Basic) o en el icono **Propiedades** (C#) para abrir el **Diseñador de proyectos**.
1. Seleccione la pestaña **Configuración**.
1. Busque la conexión que desea editar y seleccione el texto en el campo **valor** .
1. Edite la cadena de conexión en el campo **valor** o haga clic en el botón de **puntos suspensivos** (...) del campo **valor** para editar la conexión con el cuadro de diálogo Propiedades de la **conexión** .

## <a name="edit-connection-strings-for-datasets"></a>Editar cadenas de conexión para conjuntos de valores
Puede modificar la información de conexión de cada TableAdapter en un conjunto de datos.

### <a name="to-edit-a-connection-string-for-a-tableadapter-in-a-dataset"></a>Para editar una cadena de conexión para un TableAdapter en un conjunto de objetos
1. En **Explorador de soluciones**, haga doble clic en el conjunto de archivos (archivo **. xsd** ) que tenga la conexión que desea editar.
1. Seleccione el **TableAdapter** o la consulta que tiene la conexión que desea editar.
1. En la ventana **propiedades** , expanda el **nodo conexión**.
1. Para modificar rápidamente la cadena de conexión, edite la propiedad **ConnectionString** o haga clic en la flecha hacia abajo en la propiedad de **conexión** y elija **nueva conexión**.

## <a name="security"></a>de seguridad
Almacenar información confidencial (como una contraseña) en la cadena de conexión puede afectar la seguridad de la aplicación. El uso de la seguridad integrada de Windows es una forma más segura de controlar el acceso a una base de datos.
Para más información, consulte [Proteger la información de conexión](/dotnet/framework/data/adonet/protecting-connection-information).

## <a name="see-also"></a>Vea también

- [Agregar conexiones](../data-tools/add-new-connections.md)
