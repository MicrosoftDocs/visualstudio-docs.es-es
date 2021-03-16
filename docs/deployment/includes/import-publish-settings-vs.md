---
ms.openlocfilehash: 94c2c733b631ef5e727c79a6e093bb224aec38c4
ms.sourcegitcommit: 79a6be815244f1cfc7b4123afff29983fce0555c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/06/2021
ms.locfileid: "102249864"
---

1. En el equipo donde tiene el proyecto de ASP.NET abierto en Visual Studio, haga clic con el botón derecho en el proyecto en el Explorador de soluciones y elija **Publicar**.

   Si previamente ha configurado algún perfil de publicación, aparece el panel **Publicar**. Haga clic en **Nuevo** o en **Crear nuevo perfil**.

1. Seleccione la opción para importar un perfil.

   ::: moniker range=">=vs-2019"
   En el cuadro de diálogo **Importar**, haga clic en **Importar perfil**.
   ::: moniker-end
   ::: moniker range="vs-2017"
   En el cuadro de diálogo **Elegir un destino de publicación**, haga clic en **Importar perfil**.
   ::: moniker-end

   ![Elegir Publicar](../../deployment/media/tutorial-publish-tool-import-profile.png)

1. Navegue hasta la ubicación del archivo de configuración de publicación que creó en la sección anterior.

1. En el cuadro de diálogo **Importar archivo de configuración de publicación**, vaya al perfil que creó en la sección anterior, selecciónelo y haga clic en **Abrir**.

   ::: moniker range=">=vs-2019"
   Haga clic en **Finalizar** para guardar el perfil de publicación y, a continuación, haga clic en **Publicar**.

   Visual Studio comienza el proceso de implementación y la ventana Salida muestra el progreso y los resultados.

   Si recibe errores de implementación, haga clic en **Configuración** para editar la configuración. Modifique la configuración y haga clic en **Validar** para probar la nueva configuración. Si no se encuentra el nombre de host, pruebe la dirección IP en lugar del nombre de host en los campos **Servidor** y **Dirección URL de destino**.
   ::: moniker-end
   ::: moniker range="vs-2017"
   Visual Studio comienza el proceso de implementación y la ventana Salida muestra el progreso y los resultados.

   Si recibe errores de implementación, haga clic en **Configuración** para editar la configuración. Modifique la configuración y haga clic en **Validar** para probar la nueva configuración. Si no se encuentra el nombre de host, pruebe la dirección IP en lugar del nombre de host en los campos **Servidor** y **Dirección URL de destino**.
   ::: moniker-end

   ![Edite la configuración de la herramienta de publicación](../../deployment/media/tutorial-configure-publish-settings-in-tool.png)
