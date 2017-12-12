---
title: "Tutorial de configuración de Visual Studio Tools para Unity Azure| Microsoft Docs"
ms.custom: 
ms.date: 10/19/2017
ms.reviewer: crdun
ms.suite: 
ms.technology: tgt-pltfrm-cross-plat
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: BAE62C27-CA7A-4466-8738-3DB880221CE1
author: dantogno
ms.author: v-davian
manager: crdun
ms.openlocfilehash: 4e1cf47420cafda2552cdbb625d6d41626c32971
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/09/2017
---
# <a name="configure-easy-tables-in-azure"></a>Configurar tablas fáciles en Azure

Las tablas fáciles son una característica de [Azure Mobile Apps](https://azure.microsoft.com/services/app-service/mobile/) que permiten la configuración y la administración de tablas SQL directamente en la GUI de Azure Portal. Azure Mobile Apps admite muchas características, pero este ejemplo se limita a la lectura y la escritura de datos almacenados en un back-end de Azure Mobile Apps desde un proyecto de Unity.

## <a name="create-a-new-azure-mobile-app"></a>Crear una aplicación de Azure Mobile App

Inicie sesión en [Azure Portal](https://ms.portal.azure.com). Si no tiene una suscripción de Azure, la [evaluación gratuita](https://azure.microsoft.com/en-us/free/) o los créditos incluidos de [Visual Studio Dev Essentials](https://www.visualstudio.com/dev-essentials/) serán más que suficientes para completar este tutorial.

**Una vez dentro del portal:**

1. Seleccione **Nuevo > Web y móvil > Aplicación móvil > Crear**.

  ![Crear una aplicación móvil](media/vstu_azure-configure-easy-tables-image1.png)

2. Configure la nueva aplicación móvil:

  * **Nombre de la aplicación**. Esto compilará la dirección URL usada para conectarse al back-end de Azure Mobile Apps. Debe elegir un nombre único, indicado por la marca de verificación verde.

  * **Suscripción**. Elija la suscripción que la nueva aplicación móvil usará para la facturación.

  * **Grupo de recursos**. Los grupos de recursos simplifican la administración de los recursos relacionados. De forma predeterminada, Azure crea un grupo de recursos con el mismo nombre que la nueva aplicación. La configuración predeterminada funciona correctamente para el tutorial.

  *  **Plan de App Service/Ubicación**. El plan de servicio dicta la capacidad de computación, la ubicación y el costo de los recursos que Azure usa para hospedar su nueva aplicación móvil. De forma predeterminada, Azure crea un plan de servicio con algunos valores predeterminados. Esta es la opción más sencilla para este tutorial. Aun así, puede usar este menú para personalizar el plan de tarifa o la ubicación geográfica de un nuevo plan de servicio. Además, puede modificar la configuración de un plan de servicio después de implementarla.

  ![Crear una aplicación móvil](media/vstu_azure-configure-easy-tables-image2.png)

3. Seleccione **Crear** y espere unos minutos a que Azure implemente el nuevo recurso. Verá una notificación en Azure Portal cuando se haya completado la implementación.

## <a name="add-a-new-data-connection"></a>Agregar una nueva conexión de datos

4. Una vez completada la implementación, haga clic en el botón **Todos los recursos** y seleccione la aplicación móvil recién creada.

  ![Seleccione la nueva aplicación móvil](media/vstu_azure-configure-easy-tables-image3.png)

5. En la hoja que se acaba de abrir, desplácese hacia abajo en el menú de la izquierda y haga clic en el botón **Tablas fáciles**, que aparece bajo el encabezado **MÓVIL**.

  ![Seleccione Tablas fáciles](media/vstu_azure-configure-easy-tables-image4.png)

6. Haga clic en el aviso azul **Deberá configurar las API fáciles/Tablas fáciles** que se muestra en la parte superior de la hoja Tablas fáciles.

  ![Aviso que indica que se haga clic para configurar las tablas fáciles](media/vstu_azure-configure-easy-tables-image5.png)

7. Haga clic en el aviso que indica **You need a database to use Easy Tables. Click here to create one** (Necesita una base de datos para usar las tablas fáciles. Haga clic aquí para crear una).

  ![Aviso que indica que se haga clic para crear una base de datos](media/vstu_azure-configure-easy-tables-image6.png)

8. En la hoja Conexiones de datos, haga clic en el botón **Agregar**.

  ![Haga clic en el botón Agregar](media/vstu_azure-configure-easy-tables-image7.png)

9. En la hoja Agregar la conexión de datos, seleccione **Base de datos SQL**.

  ![Seleccione una base de datos SQL](media/vstu_azure-configure-easy-tables-image8.png)

10. Se abrirá una hoja para configurar una nueva base de datos SQL y servidor SQL Server:

  * **Nombre**. Escriba un nombre para la base de datos.

  * **Servidor de destino**. Haga clic en **Servidor de destino** para abrir la hoja Nuevo servidor.

      * **Nombre del servidor**. Escriba un nombre para el servidor.

      * **Inicio de sesión del administrador del servidor y contraseña**. Crear un nombre de usuario y una contraseña para el administrador del servidor.

      * **Ubicación**. Elija una ubicación cercana para el servidor.

      * Asegúrese de que la casilla **Permitir que los servicios de Azure accedan al servidor** permanezca activada.

      * Haga clic en **Seleccionar** para completar la configuración del servidor.

    * **Plan de tarifa**. Deje la configuración predeterminada para el tutorial. Esto se puede modificar más adelante.

    * **Intercalación**. Deje la configuración predeterminada.

    * Haga clic en **Seleccionar** para completar la configuración de la base de datos.

    ![Configure el servidor SQL Server y la base de datos](media/vstu_azure-configure-easy-tables-image9.png)

11. De nuevo en la hoja Agregar la conexión de datos, haga clic en **Cadena de conexión**. Cuando aparezca la hoja Cadena de conexión, deje los valores predeterminados y haga clic en **Aceptar**.

  ![Haga clic en la Cadena de conexión](media/vstu_azure-configure-easy-tables-image9.1.png)

12. De nuevo en la hoja Agregar la conexión de datos, el texto "MS_TableConnectionString" ya no debería aparecer en cursiva. Haga clic en **Aceptar** y espere unos minutos a que Azure cree la conexión de datos. Recibirá una notificación cuando finalice el proceso.

  ![Haga clic en Aceptar](media/vstu_azure-configure-easy-tables-image9.2.png)

## <a name="complete-the-easy-table-initialization"></a>Completar la inicialización de una tabla fácil

13. Una vez que se haya creado correctamente la conexión de datos, haga clic en el botón **Todos los recursos** y regrese a la aplicación móvil. Es importante que complete este paso para actualizar el aviso de configuración de tablas fáciles.

14. Desplácese hacia abajo y seleccione **Tablas fáciles** y, de nuevo, haga clic en el aviso azul **Deberá configurar las API fáciles/Tablas fáciles**.

  ![Haga clic en el aviso de Tablas fáciles](media/vstu_azure-configure-easy-tables-image5.png)

15. Esta vez, en la hoja debería aparecer el aviso "Ya tiene una conexión de datos" debajo del encabezado **1**. Debajo del encabezado **2**, active la casilla que indica **I acknowledge that this will overwrite site contents** (Acepto que se sobrescriba el contenido del sitio). Ahora haga clic en **Inicializar aplicación** y espere unos minutos a que Azure complete el proceso de inicialización. Una nueva notificación le avisará cuando finalice el proceso.

  ![Haga clic en Inicializar aplicación](media/vstu_azure-configure-easy-tables-image10.png)

## <a name="next-step"></a>Paso siguiente

* [Creación de tablas sencillas](visual-studio-tools-for-unity-azure-setup.md)
