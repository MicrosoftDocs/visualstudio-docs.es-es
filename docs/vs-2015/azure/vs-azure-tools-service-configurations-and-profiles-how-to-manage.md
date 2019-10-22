---
title: Administración de configuraciones de servicio y perfiles | Microsoft Docs
description: Aprenda a trabajar con las configuraciones de servicio y los archivos de configuración de perfiles que almacenan la configuración de los entornos de implementación y la configuración de publicación para los servicios en la nube.
author: ghogen
manager: jillfra
assetId: 7da8c551-fb06-4057-b5c7-c77f4b39d803
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 8/11/2017
ms.author: ghogen
ms.openlocfilehash: d1e21642f8ff707c81dcf2e493e0784c1c04b7ed
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62576314"
---
# <a name="how-to-manage-service-configurations-and-profiles"></a>Administración de configuraciones de servicio y perfiles
## <a name="overview"></a>Información general
Al publicar un servicio en la nube, Visual Studio almacena la información de configuración en dos tipos de archivos de configuración: configuraciones de servicio y perfiles. Las configuraciones de servicio (archivos .cscfg) almacenan valores para los entornos de implementación de un servicio en la nube de Azure. Azure emplea estos archivos de configuración para administrar sus servicios en la nube. Por otro lado, los perfiles (archivos .azurePubxml) almacenan la configuración de publicación para los servicios en la nube. Estos valores son un registro de las selecciones que realiza al usar el Asistente para la publicación y Visual Studio los usa localmente. En este tema se explica cómo trabajar con ambos tipos de archivos de configuración.

## <a name="service-configurations"></a>Configuraciones de servicio
Puede crear varias configuraciones de servicio para cada uno de los entornos de implementación. Por ejemplo, puede crear una configuración de servicio para el entorno local que emplea para ejecutar y probar una aplicación de Azure y otra configuración de servicio para el entorno de producción.

Puede agregar, eliminar, cambiar el nombre y modificar las configuraciones de servicio según sus necesidades. Puede administrarlas desde Visual Studio, como se muestra en la siguiente ilustración.

![Administrar configuraciones de servicio](./media/vs-azure-tools-service-configurations-and-profiles-how-to-manage/manage-service-config.png)

También puede abrir el cuadro de diálogo **Administrar configuraciones** en las páginas de propiedades del rol. Para abrir las propiedades de un rol en un proyecto de Azure, abra el menú contextual para ese rol y, a continuación, elija **propiedades**. En la pestaña **Configuración**, expanda la lista **Configuración de servicios** y, después, haga clic en **Administrar** para abrir el cuadro de diálogo **Administrar configuraciones**.

### <a name="to-add-a-service-configuration"></a>Para agregar una configuración de servicio
1. En el Explorador de soluciones, abra el menú contextual del proyecto de Azure y luego seleccione **Administrar configuraciones**.
   
    Aparece el cuadro de diálogo **Administrar configuraciones de servicio** .
2. Para agregar una configuración de servicio, tiene que crear una copia de una configuración existente. Para ello, elija la configuración que quiere copiar en la lista Nombre y luego seleccione **Crear copia**.
3. (Opcional) Para dar un nombre diferente a la configuración del servicio, elija la nueva configuración de servicio en la lista Nombre y luego seleccione **Cambiar nombre**. En el cuadro de texto **Nombre**, escriba el nombre que quiere usar para esta configuración de servicio y luego seleccione **Aceptar**.
   
    Se agrega un nuevo archivo de configuración de servicio denominado ServiceConfiguration.[Nuevo nombre].cscfg al proyecto de Azure en el Explorador de soluciones.

### <a name="to-delete-a-service-configuration"></a>Para eliminar una configuración de servicio
1. En el Explorador de soluciones, abra el menú contextual del proyecto de Azure y luego seleccione **Administrar configuraciones**.
   
    Aparece el cuadro de diálogo **Administrar configuraciones de servicio** .
2. Para eliminar una configuración de servicio, elija la configuración que quiere eliminar en la lista **Nombre** y luego seleccione **Quitar**. Aparece un cuadro de diálogo para verificar que desea eliminar esta configuración.
3. Seleccione **Eliminar**.
   
     Se quita el archivo de configuración de servicio del proyecto de Azure en el Explorador de soluciones.

### <a name="to-rename-a-service-configuration"></a>Para cambiar el nombre de una configuración de servicio
1. En el Explorador de soluciones, abra el menú contextual del proyecto de Azure y luego seleccione **Administrar configuraciones**.
   
    Aparece el cuadro de diálogo **Administrar configuraciones de servicio** .
2. Para dar un nombre diferente a la configuración de servicio, elija la nueva configuración de servicio en la lista **Nombre** y luego seleccione **Cambiar nombre**. En el cuadro de texto **Nombre**, escriba el nombre que quiere usar para esta configuración de servicio y luego seleccione **Aceptar**.
   
    Se cambia el nombre del archivo de configuración de servicio del proyecto de Azure en el Explorador de soluciones.

### <a name="to-change-a-service-configuration"></a>Para cambiar una configuración de servicio
* Si quiere cambiar una configuración de servicio, abra el menú contextual del rol concreto que quiere cambiar en el proyecto de Azure y luego seleccione **Propiedades**. Vea [Cómo: Configuración de los roles de un servicio en la nube de Azure con Visual Studio](vs-azure-tools-configure-roles-for-cloud-service.md) para más información.

## <a name="make-different-setting-combinations-by-using-profiles"></a>Uso de los perfiles para realizar diferentes combinaciones de valores
Mediante el uso de un perfil, puede rellenar automáticamente el **Asistente para publicación** con diferentes combinaciones de configuración para distintos fines. Por ejemplo, puede tener un perfil para depuración y otro para de compilaciones de versión. En ese caso, su perfil de **depuración** tendría **IntelliTrace** habilitado y la configuración de **depuración** seleccionada y su perfil de **versión** tendría **IntelliTrace** deshabilitado y la configuración de **versión** seleccionada. También puede usar varios perfiles para implementar un servicio con una cuenta de almacenamiento diferente.

Al ejecutar el asistente por primera vez, se crea un perfil predeterminado. Visual Studio almacena el perfil en un archivo con una extensión .azurePubXml, que se agrega al proyecto de Azure en la carpeta **Perfiles** . Si especifica manualmente diferentes opciones al ejecutar el asistente más adelante, el archivo se actualiza automáticamente. Antes de ejecutar el siguiente procedimiento, tendría que haber publicado ya su servicio en la nube al menos una vez.

### <a name="to-add-a-profile"></a>Para agregar un perfil
1. Abra el menú contextual del proyecto de Azure y seleccione **Publicar**.
2. Junto a la lista **Perfil de destino**, seleccione **Guardar perfil**, como se muestra en la ilustración siguiente. Con esto se crea un perfil.
   
    ![Crear un nuevo perfil](./media/vs-azure-tools-service-configurations-and-profiles-how-to-manage/create-new-profile.png)
3. Después de crea el perfil, haga clic en **<Administrar...>** en la lista **Perfil de destino**.
   
    Aparece el cuadro de diálogo **Administrar perfiles** , como se muestra en la ilustración siguiente.
   
    ![Administrar diálogo de perfiles](./media/vs-azure-tools-service-configurations-and-profiles-how-to-manage/manage-profiles.png)
4. En la lista **Nombre**, elija un perfil y luego seleccione **Crear copia**.
5. Elija el botón **Cerrar** .
   
    El nuevo perfil aparece en la lista de perfiles de destino.
6. En la lista **Perfil de destino** , seleccione el perfil que acaba de crear. La configuración del Asistente para publicación se rellena con las opciones del perfil seleccionado.
7. Seleccione los botones **Anterior** y **Siguiente** para mostrar cada página del Asistente para publicación y luego personalice la configuración para este perfil. Para más información vea [Asistente para publicar aplicación de Azure](http://go.microsoft.com/fwlink/p/?LinkID=623085) .
8. Cuando termine de personalizar la configuración, seleccione **Siguiente** para volver a la página de configuración. El perfil se guarda cuando se publica el servicio usando estos valores o al seleccionar **Guardar** junto a la lista de perfiles.

### <a name="to-rename-or-delete-a-profile"></a>Para cambiar el nombre de un perfil o eliminarlo 
1. Abra el menú contextual del proyecto de Azure y seleccione **Publicar**.
2. En la lista **Perfil de destino**, seleccione **Administrar**.
3. En el cuadro de diálogo **Administrar perfiles**, seleccione el perfil que quiere eliminar y luego seleccione **Quitar**.
4. En el cuadro de diálogo de confirmación que aparece, seleccione **Aceptar**.
5. Seleccione **Cerrar**.

### <a name="to-change-a-profile"></a>Para cambiar un perfil
1. Abra el menú contextual del proyecto de Azure y seleccione **Publicar**.
2. En la lista **Perfil de destino** , seleccione el perfil que quiere cambiar.
3. Seleccione los botones **Anterior** y **Siguiente** para mostrar cada página del Asistente para publicación y luego cambie los valores de configuración que quiera. Para más información vea [Asistente para publicar aplicación de Azure](http://go.microsoft.com/fwlink/p/?LinkID=623085) .
4. Cuando termine de personalizar la configuración, seleccione **Siguiente** para volver a la página **Configuración**.
5. (Opcional) Haga clic en **Publicar** para publicar el servicio en la nube con los nuevos valores de configuración. Si no desea publicar su servicio en la nube en este momento y cierra al Asistente para publicación, Visual Studio le pregunta si desea guardar los cambios en el perfil.

## <a name="next-steps"></a>Pasos siguientes
Para obtener información acerca de cómo configurar otras partes de su proyecto de Azure desde Visual Studio, consulte [Configurar un proyecto de Azure](http://go.microsoft.com/fwlink/p/?LinkID=623075)
