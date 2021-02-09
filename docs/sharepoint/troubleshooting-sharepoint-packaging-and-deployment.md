---
title: Solución de problemas de empaquetado e implementación de SharePoint | Microsoft Docs
description: Comprenda y solucione diversos problemas que pueden surgir al empaquetar e implementar soluciones de SharePoint.
ms.custom: SEO-VS-2020
ms.date: 02/22/2017
ms.topic: conceptual
f1_keywords:
- VSTO.WorkflowDeployment.Troubleshooting
- VS.SharePointTools.Project.PackageRetraction
- VS.SharePointTools.Deployment.Troubleshooting
- VS.SharePointTools.Deploying.Troubleshooting
- VS.SharePointTools.Project.DeploymentTroubleshooting
- VS.SharePointTools.Project.SharePointNotInstalled
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, packaging
- SharePoint development in Visual Studio, troubleshooting
- SharePoint development in Visual Studio, deployment conflict resolution
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: f3ef56ba868700699eaaeb8ec88291fd6f8d8d32
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99892312"
---
# <a name="troubleshoot-sharepoint-packaging-and-deployment"></a>Solucionar problemas de empaquetado e implementación de SharePoint
  En este tema se tratan diversos problemas que pueden producirse al empaquetar e implementar soluciones de SharePoint.

## <a name="enable-enhanced-debugging"></a>Habilitar depuración mejorada
 Si desea realizar un diagnóstico entre Visual Studio, SharePoint y otras capas, puede usar la clave del Registro EnableDiagnostics para ver el seguimiento de la pila. Para obtener más información, vea [depurar soluciones de SharePoint](../sharepoint/debugging-sharepoint-solutions.md).

## <a name="add-project-output-to-the-solution-package"></a>Agregar el resultado del proyecto al paquete de solución
 Puede agregar la salida del proyecto a un paquete a través del Diseñador de paquetes. Sin embargo, cuando agregue la salida del proyecto, asegúrese de que la plataforma del proyecto coincide con la plataforma de la solución de SharePoint. Se recomienda usar el destino de la plataforma **any CPU** para los ensamblados que desee implementar en un servidor de SharePoint. Para obtener más información, vea la [Página compilar, el diseñador de proyectos &#40;Visual Basic&#41;](../ide/reference/compile-page-project-designer-visual-basic.md) y el [cuadro de diálogo Configuración avanzada del compilador &#40;Visual Basic ](../ide/reference/advanced-compiler-settings-dialog-box-visual-basic.md)&#41;.

## <a name="validation-warnings-and-errors"></a>Advertencias y errores de validación
 Las herramientas de desarrollo de SharePoint de Visual Studio realizan pasos de validación para comprobar que el paquete de solución se crea de forma correcta. También puede crear pasos de validación personalizados para sus características y paquetes. Para obtener más información, vea [Cómo: para crear reglas personalizadas de validación de características y paquetes para soluciones de SharePoint](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md).

## <a name="deployment-conflict-resolution"></a>Resolución de conflictos de implementación
 Al implementar una solución de SharePoint, pueden producirse colisiones cuando un elemento del servidor tiene el mismo nombre, dirección URL o identificador que un elemento del paquete de solución. Puede cambiar la propiedad **resolución de conflictos de implementación** para resolver, notificar u omitir las colisiones de los módulos, elementos Web, instancias de lista y tipos de contenido.

 En la tabla siguiente se muestran los valores para la propiedad de **resolución de conflictos de implementación** .

|Value|Descripción|
|-----------|-----------------|
|Automático|Detecta las colisiones y resuelve los conflictos automáticamente.|
|Solicitud|Detecta las colisiones y las notifica al desarrollador de software antes de resolver los conflictos.|
|None|No detecta las colisiones.|

## <a name="differences-between-f5-deployment"></a>Diferencias entre la implementación F5
 Cuando se usa [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] para implementar un proyecto de SharePoint en el servidor de SharePoint local para su comprobación y depuración, hay algunos pasos adicionales que [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] realiza.

1. Restablece Internet Información Services (IIS) durante el paso de implementación.

2. Asocia automáticamente los flujos de trabajo.

3. Establece el orden de activación de características según la jerarquía del Diseñador de paquetes.

   Puede Agregar pasos de implementación personalizados para cambiar aún más el comportamiento de **F5** . Para obtener más información, vea [Tutorial: crear un paso de implementación personalizado para proyectos de SharePoint](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md).

## <a name="delay-displaying-sharepoint-page-when-deploy-visual-web-part"></a>Retrasar la visualización de la página de SharePoint al implementar el elemento Web Visual
 La página de SharePoint tarda mucho en aparecer cuando se implementa un elemento web visual en la carpeta Bin de [!INCLUDE[wiprlhext](../sharepoint/includes/wiprlhext-md.md)], [!INCLUDE[win7](../sharepoint/includes/win7-md.md)] o [!INCLUDE[winsvr08](../sharepoint/includes/winsvr08-md.md)]. Si se cambian los archivos de un directorio de [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] de nivel superior, como el directorio Bin, se volverá a compilar toda la aplicación web. Esto puede generar un retraso de hasta 25 segundos en la presentación de la página de SharePoint.

### <a name="error-message"></a>Mensaje de error
 Ninguno.

### <a name="resolution"></a>Solución
 Para evitar este problema, siga estos pasos:

1. Instale Update KB967535 como se describe en el artículo Soporte técnico de Microsoft [corrección: hay disponible una revisión para corregir dos problemas en ASP.net en IIS 7,0 para Windows Vista y Windows Server 2008](https://support.microsoft.com/help/967535).

2. Agregue la línea siguiente al archivo Web.config.

    ```xml
    <compilation batch="false" optimizeCompilations="true">
    ```

## <a name="sharepoint-project-deployment-fails-with-error-failed-to-extract-the-cab-file-in-the-solution"></a>Error en la implementación del proyecto de SharePoint: "no se pudo extraer el archivo CAB de la solución"
 Si el nombre de algún elemento de proyecto de SharePoint contiene paréntesis, se produce un error en la implementación de la solución.

### <a name="error-message"></a>Mensaje de error
 En el paso 'Agregar solución' de la implementación se ha producido el siguiente error: "Error al extraer el archivo cab de la solución".

### <a name="resolution"></a>Solución
 Para evitar este problema, quite los paréntesis de los nombres de elementos de proyecto de SharePoint.

## <a name="error-appears-when-deploying-a-visual-web-part-to-a-site-on-a-different-web-application"></a>Aparece un error al implementar un elemento Web visual en un sitio en una aplicación web diferente
 La primera vez que implementa un elemento web visual en un sitio de otra aplicación web distinta de la que está implementando en la actualidad (mediante la modificación de la propiedad SiteUrl del elemento web visual), se produce un error.

### <a name="error-message"></a>Mensaje de error
 En el paso 'Agregar solución' de la implementación se produce el siguiente error: "Ya se ha instalado una característica con Id. [#] en este conjunto de servidores. Use el atributo fuerza para volver a agregar la característica de modo explícito".

### <a name="resolution"></a>Solución
 Este error se produce debido al modo en que se retractan las características de elementos web visuales en SharePoint. Para implementar correctamente el elemento Web visual, vuelva a implementar la solución eligiendo la tecla **F5** .

## <a name="warning-appears-when-deploying-nested-user-controls"></a>Aparece una advertencia al implementar controles de usuario anidados
 Esta advertencia se produce al implementar una solución de SharePoint que contiene controles de usuario anidados, como un elemento web visual que incluye un control de usuario o un control de usuario que incluye un elemento web visual u otro control de usuario. Esta advertencia se produce si se agrega un control a un diseñador arrastrándolo desde el cuadro de herramientas o mediante la @Register Directiva en la vista de código fuente.

### <a name="error-message"></a>Mensaje de error
 ADVERTENCIA 1 el elemento ' [*nombre del control*] ' no es un elemento conocido. Esto se puede producir si hay un error de compilación en el sitio web o no se encuentra el archivo web.config.

### <a name="resolution"></a>Solución
 Si el [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] sistema del proyecto no es consciente de un control de usuario anidado, no puede proporcionar IntelliSense y emite la advertencia. El sistema de proyectos no reconoce un control de usuario anidado si no se ha compilado el proyecto y el diseñador no se ha cerrado y se ha vuelto a abrir, o si está habilitada la opción de retracción automática, que hace que el control de usuario se retire del subárbol de SharePoint después de la depuración.

 Para quitar esta advertencia, compile el proyecto y, a continuación, cierre el diseñador y vuelva a abrirlo, o deshabilite la opción de retracción automática en el proyecto. Para ello, desactive la casilla **retraer automáticamente después de depurar** en la pestaña **SharePoint** del cuadro de diálogo Propiedades del proyecto.

## <a name="see-also"></a>Vea también

- [Empaquetado e implementación de soluciones de SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)