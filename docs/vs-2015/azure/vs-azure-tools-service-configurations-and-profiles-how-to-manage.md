---
title: Cómo administrar las configuraciones de servicio y perfiles | Microsoft Docs
description: Obtenga información sobre cómo trabajar con archivos de configuración de perfiles y las configuraciones de servicio | que almacena la configuración de los entornos de implementación y configuración de publicación para los servicios en la nube.
author: ghogen
manager: douge
assetId: 7da8c551-fb06-4057-b5c7-c77f4b39d803
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 8/11/2017
ms.author: ghogen
ms.openlocfilehash: 3f7c7341b115f0899ac4c90d574a65dfdb4087bc
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/05/2018
ms.locfileid: "51002916"
---
# <a name="how-to-manage-service-configurations-and-profiles"></a>Administración de perfiles y configuraciones de servicio
## <a name="overview"></a>Información general
Al publicar un servicio en la nube, Visual Studio almacena información de configuración en dos tipos de archivos de configuración: configuraciones de servicio y perfiles. Las configuraciones de servicio (archivos .cscfg) almacenan valores para los entornos de implementación para un servicio de nube de Azure. Azure usa estos archivos de configuración cuando administra los servicios en la nube. Por otro lado, el almacén de perfiles (archivos .azurePubxml) la configuración de publicación de servicios en la nube. Estos valores son un registro de los que elija cuando utilice al Asistente para publicación y se usan localmente mediante Visual Studio. En este tema se explica cómo trabajar con ambos tipos de archivos de configuración.

## <a name="service-configurations"></a>Configuraciones de servicio
Puede crear varias configuraciones de servicio para cada uno de los entornos de implementación. Por ejemplo, podría crear una configuración de servicio para el entorno local que usa para ejecutar y probar una aplicación de Azure y otra configuración del servicio para el entorno de producción.

Puede agregar, eliminar, cambiar el nombre y modificar las configuraciones de servicio según sus requisitos. Puede administrar las configuraciones de servicio desde Visual Studio, tal como se muestra en la siguiente ilustración.

![Administrar configuraciones de servicio](./media/vs-azure-tools-service-configurations-and-profiles-how-to-manage/manage-service-config.png)

También puede abrir el **administrar configuraciones** cuadro de diálogo de páginas de propiedades del rol. Para abrir las propiedades de un rol en el proyecto de Azure, abra el menú contextual para ese rol y, a continuación, elija **propiedades**. En el **configuración** , expanda el **configuración del servicio** lista y, a continuación, seleccione **administrar** para abrir el **administrar configuraciones** cuadro de diálogo.

### <a name="to-add-a-service-configuration"></a>Para agregar una configuración de servicio
1. En el Explorador de soluciones, abra el menú contextual del proyecto de Azure y, a continuación, seleccione **administrar configuraciones**.
   
    El **administrar configuraciones de servicio** aparece el cuadro de diálogo.
2. Para agregar una configuración de servicio, debe crear una copia de una configuración existente. Para ello, elija la configuración que desea copiar en la lista Nombre y, a continuación, seleccione **crear copia**.
3. (Opcional) Para dar un nombre diferente a la configuración del servicio, elija la nueva configuración de servicio en la lista Nombre y, a continuación, seleccione **cambiar el nombre**. En el **nombre** texto, escriba el nombre que desea usar para esta configuración de servicio y, a continuación, seleccione **Aceptar**.
   
    Un nuevo archivo de configuración de servicio denominado ServiceConfiguration. [Nuevo nombre] .cscfg se agrega al proyecto de Azure en el Explorador de soluciones.

### <a name="to-delete-a-service-configuration"></a>Para eliminar una configuración de servicio
1. En el Explorador de soluciones, abra el menú contextual del proyecto de Azure y, a continuación, seleccione **administrar configuraciones**.
   
    El **administrar configuraciones de servicio** aparece el cuadro de diálogo.
2. Para eliminar una configuración de servicio, elija la configuración que desea eliminar de la **nombre** lista y, a continuación, seleccione **quitar**. Aparece un cuadro de diálogo para comprobar que desea eliminar esta configuración.
3. Seleccione **eliminar**.
   
     Se quita el archivo de configuración de servicio de proyecto de Azure en el Explorador de soluciones.

### <a name="to-rename-a-service-configuration"></a>Para cambiar el nombre de una configuración de servicio
1. En el Explorador de soluciones, abra el menú contextual del proyecto de Azure y, a continuación, seleccione **administrar configuraciones**.
   
    El **administrar configuraciones de servicio** aparece el cuadro de diálogo.
2. Para cambiar el nombre de una configuración de servicio, elija la nueva configuración de servicio desde el **nombre** lista y, a continuación, seleccione **cambiar el nombre**. En el **nombre** texto, escriba el nombre que desea usar para esta configuración de servicio y, a continuación, seleccione **Aceptar**.
   
    Se cambia el nombre del archivo de configuración del servicio en el proyecto de Azure en el Explorador de soluciones.

### <a name="to-change-a-service-configuration"></a>Para cambiar una configuración de servicio
* Si desea cambiar una configuración de servicio, abra el menú contextual del rol concreto que desea cambiar en el proyecto de Azure y, a continuación, seleccione **propiedades**. Consulte [Cómo: configurar los Roles para un servicio de nube de Azure con Visual Studio](vs-azure-tools-configure-roles-for-cloud-service.md) para obtener más información.

## <a name="make-different-setting-combinations-by-using-profiles"></a>Asegúrese de diferentes combinaciones de valores mediante el uso de perfiles
Mediante el uso de un perfil, puede rellenar automáticamente el **Asistente para publicación** con diferentes combinaciones de configuración para distintos fines. Por ejemplo, puede tener un perfil para la depuración y otra para la versión se basa. En ese caso, su **depurar** tendría perfil **IntelliTrace** habilitado y el **depurar** configuración seleccionada y su **versión** perfil tendría **IntelliTrace** deshabilitado y el **versión** configuración seleccionada. También puede usar distintos perfiles para implementar un servicio con una cuenta de almacenamiento diferente.

Al ejecutar el asistente por primera vez, se crea un perfil predeterminado. Visual Studio almacena el perfil en un archivo que tiene una extensión .azurePubXml, que se agrega al proyecto de Azure bajo la **perfiles** carpeta. Si especifica manualmente diferentes opciones al ejecutar el asistente más adelante, el archivo se actualiza automáticamente. Antes de ejecutar el siguiente procedimiento, debe ya haya publicado su servicio en la nube al menos una vez.

### <a name="to-add-a-profile"></a>Para agregar un perfil
1. Abra el menú contextual del proyecto de Azure y, a continuación, seleccione **publicar**.
2. Junto a la **perfil objetivo** lista, seleccione el **Guardar perfil** botón, como se muestra en la ilustración siguiente. Esto crea un perfil.
   
    ![Crear un nuevo perfil](./media/vs-azure-tools-service-configurations-and-profiles-how-to-manage/create-new-profile.png)
3. Una vez creado el perfil, seleccione **< administrar … >** en el **perfil objetivo** lista.
   
    El **administrar perfiles** aparece el cuadro de diálogo, como se muestra en la ilustración siguiente.
   
    ![Administrar diálogo de perfiles](./media/vs-azure-tools-service-configurations-and-profiles-how-to-manage/manage-profiles.png)
4. En el **nombre** lista, elija un perfil y, a continuación, seleccione **crear copia**.
5. Elija la **cerrar** botón.
   
    El nuevo perfil aparece en la lista de perfiles de destino.
6. En el **perfil objetivo** lista, seleccione el perfil que acaba de crear. La configuración del Asistente para publicación se rellena con las opciones del perfil seleccionado.
7. Seleccione el **anterior** y **siguiente** botones para mostrar cada página del Asistente para publicación y, a continuación, personalizar la configuración para este perfil. Consulte [asistente Publicar aplicación de Azure](http://go.microsoft.com/fwlink/p/?LinkID=623085) para obtener información.
8. Cuando termine de personalizar la configuración, seleccione **siguiente** para volver a la página de configuración. El perfil se guarda cuando se publica el servicio utilizando estos valores o si selecciona **guardar** junto a la lista de perfiles.

### <a name="to-rename-or-delete-a-profile"></a>Cambiar el nombre o eliminar un perfil
1. Abra el menú contextual del proyecto de Azure y, a continuación, seleccione **publicar**.
2. En el **perfil objetivo** lista, seleccione **administrar**.
3. En el **administrar perfiles** cuadro de diálogo, seleccione el perfil que desea eliminar y luego seleccione **quitar**.
4. En el cuadro de diálogo de confirmación que aparece, seleccione **Aceptar**.
5. Seleccione **cerrar**.

### <a name="to-change-a-profile"></a>Para cambiar un perfil
1. Abra el menú contextual del proyecto de Azure y, a continuación, seleccione **publicar**.
2. En el **perfil objetivo** lista, seleccione el perfil que desea cambiar.
3. Seleccione el **anterior** y **siguiente** botones para mostrar cada página del Asistente para publicación y, a continuación, cambie la configuración que desee. Consulte [asistente Publicar aplicación de Azure](http://go.microsoft.com/fwlink/p/?LinkID=623085) para obtener información.
4. Cuando termine de cambiar la configuración, seleccione **siguiente** para volver a la **configuración** página.
5. (Opcional) seleccione **publicar** para publicar el servicio en la nube con la nueva configuración. Si no desea publicar su servicio en la nube en este momento y cierra al Asistente para publicación, Visual Studio le pregunta si desea guardar los cambios en el perfil.

## <a name="next-steps"></a>Pasos siguientes
Para obtener información acerca de cómo configurar otras partes de su proyecto de Azure desde Visual Studio, consulte [configurar un proyecto de Azure](http://go.microsoft.com/fwlink/p/?LinkID=623075)

