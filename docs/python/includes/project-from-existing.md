---
ms.topic: include
ms.openlocfilehash: 47c390fbc7a6f84c25d4bde0317985bd149cae2f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "89323442"
---
1. Inicie Visual Studio y seleccione **Archivo** > **Nuevo** > **Proyecto**.

1. En el cuadro de diálogo **Nuevo proyecto**, busque "Python", seleccione la plantilla **Desde código de Python existente**, asigne al proyecto un nombre y una ubicación y, después, haga clic en **Aceptar**.

1. En el asistente que aparece, establezca la ruta de acceso al código existente, así como un filtro para tipos de archivo, especifique una ruta de acceso de búsqueda que requiera el proyecto y, después, seleccione **Siguiente**. Si no sabe cuáles son las rutas de acceso de búsqueda, deje ese campo en blanco.

    ![Nuevo proyecto a partir de código existente, paso 1](../media/projects-from-existing-1.png)

1. En el siguiente cuadro de diálogo, seleccione el archivo de inicio para el proyecto y, después, **Siguiente**. Si quiere, seleccione un entorno; en caso contrario, acepte los valores predeterminados. Tenga en cuenta que el cuadro de diálogo solo muestra los archivos del directorio raíz; si el archivo que quiere está en una subcarpeta, deje el archivo de inicio en blanco y establézcalo posteriormente en el **Explorador de soluciones** (descrito a continuación).

    ![Nuevo proyecto a partir de código existente, paso 2](../media/projects-from-existing-2.png)

1. Seleccione la ubicación en la que se va a guardar el archivo del proyecto (un archivo *.pyproj* en disco). Si procede, también puede incluir la detección automática de entornos virtuales y personalizar el proyecto para marcos web diferentes. Si no conoce estas opciones, déjelas con los valores predeterminados.

    ![Nuevo proyecto a partir de código existente, paso 3](../media/projects-from-existing-3.png)

1. Haga clic en **Finalizar**. Visual Studio creará el proyecto y lo abrirá en el **Explorador de soluciones**. Si quiere mover el archivo *.pyproj* a otra parte, selecciónelo en el **Explorador de soluciones** y elija **Archivo** > **Guardar como**. Esta acción actualiza las referencias de archivo en el proyecto pero no mueve ningún archivo de código.

1. Para establecer otro archivo de inicio, localice el archivo en el **Explorador de soluciones**, haga clic con el botón derecho y seleccione **Establecer como archivo de inicio**.