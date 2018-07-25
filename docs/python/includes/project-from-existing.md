---
ms.topic: include
ms.openlocfilehash: 37079cfaa1204cd8ce7a77e1e2f5aa91ea844ea5
ms.sourcegitcommit: c57ae28181ffe14a30731736661bf59c3eff1211
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/11/2018
ms.locfileid: "38809423"
---
1. Inicie Visual Studio y seleccione **Archivo > Nuevo > Proyecto**.

1. En el cuadro de diálogo **Nuevo proyecto**, busque "Python", seleccione la plantilla "Desde código de Python existente", asigne al proyecto un nombre y una ubicación y, después, seleccione **Aceptar**.

1. En el asistente que aparece, establezca la ruta de acceso al código existente, así como un filtro para tipos de archivo, especifique una ruta de acceso de búsqueda que requiera el proyecto y, después, seleccione **Siguiente**. Si no sabe cuáles son las rutas de acceso de búsqueda, deje ese campo en blanco.

    ![Nuevo proyecto a partir de código existente, paso 1](../media/projects-from-existing-1.png)

1. En el siguiente cuadro de diálogo, seleccione el archivo de inicio para el proyecto y, después, **Siguiente**. Si quiere, seleccione un entorno; en caso contrario, acepte los valores predeterminados. Tenga en cuenta que el cuadro de diálogo solo muestra los archivos del directorio raíz; si el archivo que quiere está en una subcarpeta, deje el archivo de inicio en blanco y establézcalo posteriormente en el Explorador de soluciones (descrito a continuación).

    ![Nuevo proyecto a partir de código existente, paso 2](../media/projects-from-existing-2.png)

1. Seleccione la ubicación en la que se va a guardar el archivo del proyecto (un archivo `.pyproj` en disco). Si procede, también puede incluir la detección automática de entornos virtuales y personalizar el proyecto para marcos web diferentes. Si no conoce estas opciones, déjelas con los valores predeterminados.

    ![Nuevo proyecto a partir de código existente, paso 3](../media/projects-from-existing-3.png)

1. Seleccione **Finalizar**. Visual Studio creará el proyecto y lo abrirá en el Explorador de soluciones. Si quiere mover el archivo `.pyproj` a otra parte, selecciónelo en el Explorador de soluciones y pulse **Archivo > Guardar como**. Esta acción actualiza las referencias de archivo en el proyecto pero no mueve ningún archivo de código.

1. Para establecer otro archivo de inicio, localice el archivo en el Explorador de soluciones, haga clic con el botón derecho y seleccione **Establecer como archivo de inicio**.