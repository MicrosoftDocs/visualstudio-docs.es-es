---
title: Publicar un servicio en la nube mediante Azure Tools | Microsoft Docs
description: Obtenga información sobre cómo publicar proyectos de servicio de nube de Azure mediante Visual Studio.
author: ghogen
manager: douge
assetId: 1a07b6e4-3678-4cbf-b37e-4520b402a3d9
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 11/11/2017
ms.author: ghogen
ms.openlocfilehash: cf29e1cdde71d2e8ef7caa9bc91bc31c30c7bc41
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/05/2018
ms.locfileid: "51002856"
---
# <a name="publishing-a-cloud-service-using-visual-studio"></a>Publicación de un servicio en la nube con Visual Studio

Visual Studio puede publicar una aplicación directamente en Azure, con compatibilidad para entornos de ensayo y producción de un servicio en la nube. Al publicar, seleccione el entorno de implementación y una cuenta de almacenamiento que se utiliza temporalmente para el paquete de implementación.

Cuando desarrolla y prueba una aplicación de Azure, puede usar Web Deploy para publicar los cambios de sus roles web incrementalmente. Después de publicar la aplicación en un entorno de implementación, Web Deploy le permite implementar los cambios directamente en la máquina virtual que se está ejecutando el rol web. No es necesario empaquetar y publicar la aplicación de Azure completa cada vez que desee para actualizar su rol web para probar los cambios. Con este enfoque, puede tener los cambios del rol web disponibles en la nube para pruebas sin tener que esperar para que la aplicación publicada en un entorno de implementación.

Use los procedimientos siguientes para publicar su aplicación de Azure y para actualizar un rol web mediante Web Deploy:

- Publicar o empaquetar una aplicación de Azure desde Visual Studio
- Actualizar un rol web como parte del ciclo de desarrollo y pruebas

## <a name="publish-or-package-an-azure-application-from-visual-studio"></a>Publicar o empaquetar una aplicación de Azure desde Visual Studio

Al publicar su aplicación de Azure, puede realizar una de las tareas siguientes:

- Crear un paquete de servicio: puede usar este paquete y el archivo de configuración de servicio para publicar la aplicación en un entorno de implementación desde el [portal Azure](https://portal.azure.com).

- Publicar su proyecto de Azure desde Visual Studio: para publicar la aplicación directamente en Azure, use el Asistente para publicación. Para obtener información, consulte [asistente Publicar aplicación de Azure](vs-azure-tools-publish-azure-application-wizard.md).

### <a name="to-create-a-service-package-from-visual-studio"></a>Para crear un paquete de servicio desde Visual Studio

1. Cuando esté listo para publicar la aplicación, abra el Explorador de soluciones, abra el menú contextual del proyecto de Azure que contiene sus roles y elija Publicar.

1. Para crear un paquete de servicio sólo, siga estos pasos:

   a. En el menú contextual del proyecto de Azure, elija **paquete**.

   b. En el **empaquetar aplicación de Azure** cuadro de diálogo, elija la configuración del servicio para el que desea crear un paquete y, a continuación, elija la configuración de compilación.

   c. (Opcional) Para activar el escritorio remoto para el servicio en la nube después de haberlo publicado, seleccione **habilitar Escritorio remoto para todos los Roles**y, a continuación, seleccione **configuración** para configurar las credenciales de escritorio remoto. Para obtener más información, consulte [Habilitar conexión a Escritorio remoto para un rol en Azure Cloud Services mediante Visual Studio](/azure/cloud-services/cloud-services-role-enable-remote-desktop-visual-studio).

      Si desea depurar el servicio de nube después de haberlo publicado, activar la depuración remota seleccionando **habilitar depurador remoto para todos los Roles**.

   d. Para crear el paquete, elija el **paquete** vínculo.

      Explorador de archivos muestra la ubicación del archivo del paquete recién creado. Puede copiar esta ubicación para que se puede usar desde el portal de Azure.

   e. Para publicar este paquete en un entorno de implementación, debe usar esta ubicación como la ubicación del paquete al crear un servicio en la nube e implementar este paquete en un entorno con el portal de Azure.

1. (Opcional) Para cancelar el proceso de implementación, en el menú contextual para el elemento de línea en el registro de actividad, elija **Cancelar y quitar**. Este comando detiene el proceso de implementación y elimina el entorno de implementación de Azure. Para quitar el entorno después de la implementación, use el portal de Azure.

1. (Opcional) Después de que hayan iniciado las instancias de rol, Visual Studio muestra automáticamente el entorno de implementación en el **servicios en la nube** nodo en el Explorador de servidores. Desde aquí, puede ver el estado de las instancias de rol individuales. Consulte [recursos de administración de Azure con Cloud Explorer](vs-azure-tools-resources-managing-with-cloud-explorer.md). La siguiente ilustración muestra las instancias de rol mientras todavía están en estado Initializing:

    ![VST_DeployComputeNode](./media/vs-azure-tools-publishing-a-cloud-service/IC744134.png)

## <a name="update-a-web-role-as-part-of-the-development-and-testing-cycle"></a>Actualizar un rol web como parte del ciclo de desarrollo y pruebas

Si la infraestructura de back-end de la aplicación es estable, pero los roles web necesitan actualizaciones más frecuentes, puede usar Web Deploy para actualizar solo un rol web en el proyecto. Web Deploy resulta práctico cuando no desea recompilar e implementar los roles de trabajo de back-end, o si tiene varios roles web y desea actualizar solo uno de los roles web.

### <a name="requirements-for-using-web-deploy"></a>Requisitos para usar Web Deploy

- **Solo con fines de desarrollo y pruebas**: los cambios se realizan directamente en la máquina virtual que se ejecuta el rol web. Si esta máquina virtual tiene que ser reciclada, se pierden los cambios porque el paquete original que publicó se usa para volver a crear la máquina virtual para el rol. Vuelva a publicar la aplicación para obtener los cambios más recientes para el rol web.

- **Se pueden actualizar solo los roles web**: no se puede actualizar los roles de trabajo. Además, no puede actualizar el `RoleEntryPoint` en `web role.cs`.

- **Solo puede admitir una única instancia de un rol web**: no puede tener varias instancias de ningún rol web en su entorno de implementación. Sin embargo, se admiten varios roles de web, cada uno con una única instancia.

- **Habilitar las conexiones a escritorio remotas**: este requisito permite que Web Deploy utilice el usuario y contraseña para conectarse a la máquina virtual para implementar los cambios en el servidor que ejecuta Internet Information Services (IIS). Además, es posible que deba conectarse a la máquina virtual para agregar un certificado de confianza a IIS en esta máquina virtual. (Este certificado asegura que la conexión remota de IIS que usa Web Deploy sea segura).

El siguiente procedimiento se da por supuesto que está usando el **publicar aplicación de Azure** asistente.

### <a name="enable-web-deploy-when-you-publish-your-application"></a>Habilitar Web Deploy al publicar su aplicación

1. Para habilitar el **habilitar Web Deploy para todos los roles web** opción, primero debe configurar las conexiones a escritorio remotas. Seleccione **habilitar Escritorio remoto** para todos los roles y, a continuación, proporcione las credenciales que se usa para conectarse de forma remota en el **configuración de escritorio remoto** cuadro que aparece. Consulte [Habilitar conexión a Escritorio remoto para un rol en Azure Cloud Services mediante Visual Studio](/azure/cloud-services/cloud-services-role-enable-remote-desktop-visual-studio).

1. Para habilitar Web Deploy para todos los roles web en la aplicación, seleccione **habilitar Web Deploy para todos los roles web**.

    Aparece un triángulo de advertencia amarillo. Web Deploy usa un certificado autofirmado, que no se confía de forma predeterminada, que no se recomienda para cargar los datos confidenciales. Si necesita proteger este proceso para datos confidenciales, puede agregar un certificado SSL que se usará para las conexiones de Web Deploy. Este certificado debe ser un certificado de confianza. Para obtener más información, consulte [proteger web deploy](#make-web-deploy-secure).

1. Elija **siguiente** para mostrar el **resumen** pantalla y, a continuación, elija **publicar** para implementar el servicio en la nube.

    Se publica el servicio en la nube. La máquina virtual que se crea tiene conexiones remotas habilitadas para IIS para que Web Deploy puede usarse para actualizar sus roles web sin volver a publicarlos.

   > [!NOTE]
   > Si tiene configurada más de una instancia para un rol web, aparece un mensaje de advertencia que indica que cada rol web se limita a una instancia solo en el paquete que se crea para publicar la aplicación. Seleccione **Aceptar** para continuar. Como se indicó en la sección de requisitos, puede tener más de un rol web, pero solo una instancia de cada rol.

### <a name="update-your-web-role-by-using-web-deploy"></a>Actualizar su rol web mediante Web Deploy

1. Para utilizar Web Deploy, realice los cambios de código en el proyecto para cualquiera de sus roles web en Visual Studio que desea publicar y, a continuación, haga clic en este nodo del proyecto en la solución y elija **publicar**. El **publicación Web** aparece el cuadro de diálogo.

1. (Opcional) Si agrega un certificado SSL de confianza que se utilizará para las conexiones remotas de IIS, puede desactivar la **permitir certificado de confianza** casilla de verificación. Para obtener información sobre cómo agregar un certificado para proteger Web Deploy, vea la sección **para proteger Web Deploy** más adelante en este artículo.

1. Para utilizar Web Deploy, el mecanismo de publicación necesita el nombre de usuario y la contraseña que configuró para la conexión a Escritorio remoto cuando publicó el paquete por primera vez.

   a. En **nombre de usuario**, escriba el nombre de usuario.

   b. En **contraseña**, escriba la contraseña.

   c. (Opcional) Si desea guardar esta contraseña en este perfil, elija **Guardar contraseña**.

1. Para publicar los cambios en el rol web, elija **publicar**.

    Muestra la línea de estado **publicación iniciada**. Cuando haya finalizado la publicación, **publicación correcta** aparece. Ahora, los cambios se han implementado en el rol web en la máquina virtual. Ahora puede iniciar la aplicación de Azure en el entorno de Azure para probar los cambios.

### <a name="make-web-deploy-secure"></a>Proteger web deploy

1. Web Deploy usa un certificado autofirmado, que no se confía de forma predeterminada, que no se recomienda para cargar los datos confidenciales. Si necesita proteger este proceso para datos confidenciales, puede agregar un certificado SSL que se usará para las conexiones de Web Deploy. Este certificado debe ser un certificado de confianza, que se obtiene de una entidad de certificación (CA).

    Para proteger Web Deploy para cada máquina virtual para cada uno de sus roles web, debe cargar el certificado de confianza que desea utilizar para web implementar en Azure portal. Este certificado se asegura de que el certificado se agrega a la máquina virtual que se crea para el rol web al publicar su aplicación.

1. Para agregar un certificado SSL de confianza a IIS que se utilizará para las conexiones remotas, siga estos pasos:

   a. Para conectarse a la máquina virtual que se está ejecutando el rol web, seleccione la instancia de rol web en **Cloud Explorer** o **Explorador de servidores**y, a continuación, elija el **conectar utilizando Escritorio remoto**  comando. Para obtener instrucciones detalladas sobre cómo conectarse a la máquina virtual, consulte [Habilitar conexión a Escritorio remoto para un rol en Azure Cloud Services mediante Visual Studio](/azure/cloud-services/cloud-services-role-enable-remote-desktop-visual-studio). El explorador le pide que descargue un `.rdp` archivo.

   b. Para agregar un certificado SSL, abra el servicio de administración en el Administrador de IIS. En el Administrador de IIS, habilite SSL abriendo el **enlaces** vincular en el **acción** panel. El **Agregar enlace de sitio** aparece el cuadro de diálogo. Elija **agregar**y, a continuación, seleccione HTTPS en el **tipo** lista desplegable. En el **certificado SSL** lista, elija el certificado SSL que obtuvo, firmado por una entidad de certificación y que cargó en el portal de Azure. Para obtener más información, consulte [configurar opciones de conexión para el servicio de administración](http://go.microsoft.com/fwlink/?LinkId=215824).

      > [!NOTE]
      > Si agrega un certificado SSL de confianza, el triángulo de advertencia amarillo ya no aparece en el **Asistente para publicación**.

## <a name="include-files-in-the-service-package"></a>Incluir archivos en el paquete de servicio

Es posible que deba incluir archivos específicos en el paquete de servicio para que estén disponibles en la máquina virtual que se crea para un rol. Por ejemplo, desea agregar un `.exe` o un `.msi` archivo que se usa un script de inicio para el paquete de servicio. O bien, es posible que deba agregar un ensamblado que requiera un proyecto de rol web, rol o de trabajo. Para incluir archivos, debe agregarse a la solución para su aplicación de Azure.

1. Para agregar un ensamblado a un paquete de servicio, utilice los pasos siguientes:

   a. En **el Explorador de soluciones**, abra el nodo de proyecto para el proyecto que le falta el ensamblado que se hace referencia.
   b. Para agregar el ensamblado al proyecto, abra el menú contextual para el **referencias** carpeta y, a continuación, elija **Agregar referencia**. Aparece el cuadro de diálogo Agregar referencia.
   c. Elija la referencia que desee agregar y, a continuación, elija **Aceptar**. La referencia se agrega a la lista bajo el **referencias** carpeta.
   d. Abra el menú contextual para el ensamblado que agregó y elija **propiedades**. El **propiedades** aparecerá la ventana.

      Para incluir este ensamblado en el paquete de servicio, en el **lista Copy Local** elija **True**.
1. En **el Explorador de soluciones** abra el nodo de proyecto para el proyecto que le falta el ensamblado que se hace referencia.

1. Para agregar el ensamblado al proyecto, abra el menú contextual para el **referencias** carpeta y, a continuación, elija **Agregar referencia**. El **Agregar referencia** aparece el cuadro de diálogo.

1. Elija la referencia que desee agregar y, a continuación, elija el **Aceptar** botón.

    La referencia se agrega a la lista bajo el **referencias** carpeta.

1. Abra el menú contextual para el ensamblado que agregó y elija **propiedades**. Aparece la ventana Propiedades.

1. Para incluir este ensamblado en el paquete de servicio, en el **Copy Local** elija **True**.

1. Para incluir archivos en el paquete de servicio que se han agregado al proyecto de rol web, abra el menú contextual para el archivo y, a continuación, elija **propiedades**. Desde el **propiedades** ventana, elija **contenido** desde el **acción de compilación** cuadro de lista.

1. Para incluir archivos en el paquete de servicio que se han agregado al proyecto de rol de trabajo, abra el menú contextual para el archivo y, a continuación, elija **propiedades**. Desde el **propiedades** ventana, elija **copiar si es posterior** desde el **copiar en el directorio de salida** cuadro de lista.

## <a name="next-steps"></a>Pasos siguientes

Para obtener más información acerca de la publicación en Azure desde Visual Studio, consulte [asistente Publicar aplicación de Azure](vs-azure-tools-publish-azure-application-wizard.md).
