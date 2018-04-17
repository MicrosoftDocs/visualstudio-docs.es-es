---
title: Solución de problemas de SharePoint de empaquetado e implementación | Documentos de Microsoft
ms.custom: ''
ms.date: 02/22/2017
ms.technology:
- office-development
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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 95dfd93433fc70895baa9056ce1b1522845bf497
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="troubleshooting-sharepoint-packaging-and-deployment"></a>Solucionar problemas de empaquetado e implementación de SharePoint
  En este tema se tratan diversos problemas que pueden producirse al empaquetar e implementar soluciones de SharePoint.

## <a name="enabling-enhanced-debugging"></a>Habilitar la depuración mejorada
 Si desea realizar un diagnóstico entre Visual Studio, SharePoint y otras capas, puede usar la clave del Registro EnableDiagnostics para ver el seguimiento de la pila. Para obtener más información, consulte [depurar soluciones de SharePoint](../sharepoint/debugging-sharepoint-solutions.md).

## <a name="adding-project-output-to-the-solution-package"></a>Agregar la salida del proyecto al paquete de solución
 Puede agregar la salida del proyecto a un paquete a través del Diseñador de paquetes. Sin embargo, cuando agregue la salida del proyecto, asegúrese de que la plataforma del proyecto coincide con la plataforma de la solución de SharePoint. Se recomienda que realice la **cualquier CPU** plataforma de destino para los ensamblados que desea implementar en un servidor de SharePoint. Para obtener más información, consulte [página compilación, Diseñador de proyectos &#40;Visual Basic&#41; ](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) y [cuadro de diálogo de configuración de compilador avanzada &#40;Visual Basic&#41;](/visualstudio/ide/reference/advanced-compiler-settings-dialog-box-visual-basic).

## <a name="validation-warnings-and-errors"></a>Errores y advertencias de validación
 Las herramientas de desarrollo de SharePoint de Visual Studio realizan pasos de validación para comprobar que el paquete de solución se crea de forma correcta. También puede crear pasos de validación personalizados para sus características y paquetes. Para obtener más información, consulte [Cómo: Create Custom Feature y reglas de validación de paquetes para soluciones de SharePoint](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md).

## <a name="deployment-conflict-resolution"></a>Resolución de conflictos de implementación
 Al implementar una solución de SharePoint, pueden producirse colisiones cuando un elemento del servidor tiene el mismo nombre, dirección URL o identificador que un elemento del paquete de solución. Puede cambiar la **Deployment Conflict Resolution** propiedad para resolver, notificar u omitir las colisiones de módulos, elementos Web, instancias de lista y tipos de contenido.

 En la tabla siguiente se muestra los valores para la **Deployment Conflict Resolution** propiedad.

|Valor|Descripción|
|-----------|-----------------|
|Automático|Detecta las colisiones y resuelve los conflictos automáticamente.|
|Preguntar|Detecta las colisiones y las notifica al desarrollador de software antes de resolver los conflictos.|
|Ninguna|No detecta las colisiones.|

## <a name="differences-between-f5-deployment"></a>Diferencias entre la implementación y F5
 Cuando se usa [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] para implementar un proyecto de SharePoint en el servidor de SharePoint local para su comprobación y depuración, hay algunos pasos adicionales que [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] realiza.

1.  Restablece Internet Información Services (IIS) durante el paso de implementación.

2.  Asocia automáticamente los flujos de trabajo.

3.  Establece el orden de activación de características según la jerarquía del Diseñador de paquetes.

 Puede agregar pasos de implementación personalizados para cambiar el comportamiento de F5. Para obtener más información, consulte [Tutorial: crear un paso de implementación personalizado para proyectos de SharePoint de](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md).

## <a name="delay-displaying-sharepoint-page-when-deploying-visual-web-part"></a>Retrasar la aparición de la página de SharePoint al implementar un elemento web visual
 La página de SharePoint tarda mucho en aparecer cuando se implementa un elemento web visual en la carpeta Bin de [!INCLUDE[wiprlhext](../sharepoint/includes/wiprlhext-md.md)], [!INCLUDE[win7](../sharepoint/includes/win7-md.md)] o [!INCLUDE[winsvr08](../sharepoint/includes/winsvr08-md.md)]. Si se cambian los archivos de un directorio de [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] de nivel superior, como el directorio Bin, se volverá a compilar toda la aplicación web. Esto puede generar un retraso de hasta 25 segundos en la presentación de la página de SharePoint.

### <a name="error-message"></a>Mensaje de error
 Ninguno.

### <a name="resolution"></a>Resolución
 Para evitar este problema, siga estos pasos:

1.  Instale la actualización KB967535 tal como se describe en el artículo de Microsoft Support [corregir: hay una revisión solucionar estos dos problemas en ASP.NET en IIS 7.0 para Windows Vista y Windows Server 2008](http://go.microsoft.com/fwlink/?LinkId=179055).

2.  Agregue la línea siguiente al archivo Web.config.

    ```
    <compilation batch="false" optimizeCompilations="true">
    ```

## <a name="sharepoint-project-deployment-fails-with-error-failed-to-extract-the-cab-file-in-the-solution"></a>Al implementar del proyecto de SharePoint se produce el siguiente error: "Error al extraer el archivo cab de la solución"
 Si el nombre de algún elemento de proyecto de SharePoint contiene paréntesis, se produce un error en la implementación de la solución.

### <a name="error-message"></a>Mensaje de error
 En el paso 'Agregar solución' de la implementación se ha producido el siguiente error: "Error al extraer el archivo cab de la solución".

### <a name="resolution"></a>Resolución
 Para evitar este problema, quite los paréntesis de los nombres de elementos de proyecto de SharePoint.

## <a name="error-appears-when-deploying-a-visual-web-part-to-a-site-on-a-different-web-application"></a>Aparece un error al implementar un elemento web visual en un sitio de una aplicación web diferente
 La primera vez que implementa un elemento web visual en un sitio de otra aplicación web distinta de la que está implementando en la actualidad (mediante la modificación de la propiedad SiteUrl del elemento web visual), se produce un error.

### <a name="error-message"></a>Mensaje de error
 En el paso 'Agregar solución' de la implementación se produce el siguiente error: "Ya se ha instalado una característica con Id. [#] en este conjunto de servidores. Use el atributo fuerza para volver a agregar la característica de modo explícito".

### <a name="resolution"></a>Resolución
 Este error se produce debido al modo en que se retractan las características de elementos web visuales en SharePoint. Para implementar el elemento web visual correctamente, implemente de nuevo la solución. Para ello, presione la tecla F5.

## <a name="warning-appears-when-deploying-nested-user-controls"></a>Aparece una advertencia al implementar controles de usuario anidados
 Esta advertencia se produce al implementar una solución de SharePoint que contiene controles de usuario anidados, como un elemento web visual que incluye un control de usuario o un control de usuario que incluye un elemento web visual u otro control de usuario. Esta advertencia se produce si agrega un control a un diseñador arrastrándolo desde el cuadro de herramientas o mediante el @Register la directiva en la vista del origen.

### <a name="error-message"></a>Mensaje de error
 Advertencia 1 el elemento ' [*nombre del Control*]' no es un elemento conocido. Esto se puede producir si hay un error de compilación en el sitio web o no se encuentra el archivo web.config.

### <a name="resolution"></a>Resolución
 Si el [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] sistema del proyecto no es consciente de un control de usuario anidado, no puede proporcionar IntelliSense y emite la advertencia. El sistema del proyecto no tiene constancia de un control de usuario anidado si no se compila el proyecto y el diseñador no se cierra y se volverán a abrirse, o si la retracción automática está habilitada, lo que hace que el control de usuario se retire del subárbol de SharePoint después de depurar.

 Para quitar esta advertencia, compile el proyecto y, a continuación, cierre el diseñador y vuelva a abrirlo, o deshabilite la opción de retracción automática en el proyecto. Para ello, desactive la **retraer automáticamente después de depurar** casilla de verificación en la **SharePoint** ficha del cuadro de diálogo de propiedades del proyecto.

## <a name="see-also"></a>Vea también
 [Empaquetar e implementar soluciones de SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)


