---
title: Manifiestos de aplicación para soluciones de Office
description: Obtenga información sobre cómo un manifiesto de aplicación es un archivo XML que describe los ensamblados que se cargan en una solución Microsoft Office.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: b3fbea6df2b66a108a048332e28a623bdaa95786
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99839033"
---
# <a name="application-manifests-for-office-solutions"></a>Manifiestos de aplicación para soluciones de Office
  Un manifiesto de aplicación es un archivo XML que describe los ensamblados que se cargan en una solución de Microsoft Office. Las herramientas de desarrollo de Microsoft Office en Visual Studio usan el [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] esquema del manifiesto de aplicación definido en la referencia de [manifiesto de aplicación ClickOnce](../deployment/clickonce-application-manifest.md) .

 Los manifiestos de aplicación para soluciones de Office usan los siguientes elementos y atributos [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] .

|Elemento|Descripción|Atributos|
|-------------|-----------------|----------------|
|[&#60;elemento&#62; de ensamblado &#40;aplicación ClickOnce&#41;](../deployment/assembly-element-clickonce-deployment.md)|Necesario. Elemento de nivel superior.|**manifestVersion**|
|[&#60;assemblyIdentity&#62; elemento &#40;aplicación ClickOnce&#41;](../deployment/assemblyidentity-element-clickonce-deployment.md)|Necesario. Identifica el ensamblado principal de la aplicación [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] .|**name**<br /><br /> **version**<br /><br /> **publicKeyToken**<br /><br /> **processorArchitecture**<br /><br /> **language**|
|[&#60;elemento&#62; trustInfo &#40;aplicación ClickOnce&#41;](../deployment/trustinfo-element-clickonce-application.md)|Identifica los requisitos de seguridad de la aplicación.|None|
|[&#60;elemento&#62; entryPoint &#40;aplicación ClickOnce&#41;](../deployment/entrypoint-element-clickonce-application.md)|Necesario. Identifica el punto de entrada del código de aplicación para la ejecución.|**name**<br /><br /> **dependencyName**<br /><br /> **customHostSpecified**|
|[&#60;elemento&#62; de dependencia &#40;aplicación ClickOnce&#41;](../deployment/dependency-element-clickonce-deployment.md)|Necesario. Identifica cada dependencia necesaria para que se ejecute la aplicación. Identifica opcionalmente los ensamblados que se tienen que preinstalar.|None|
|[&#60;elemento&#62; de archivo &#40;aplicación ClickOnce&#41;](../deployment/file-element-clickonce-application.md)|Necesario. Identifica cada archivo que no es de ensamblado y que se usa por la aplicación. Puede incluir datos de aislamiento del modelo de objetos componentes (COM) asociados al archivo.|**name**<br /><br /> **size**|

 Los manifiestos de aplicación para soluciones de Office tienen el siguiente elemento en el espacio de nombres `co.v1` .

```xml
<entryPoint>
    <co.v1:customHostSpecified />
</entryPoint>
```

 Estos manifiestos de aplicación también tienen los siguientes elementos y atributos en el espacio de nombres `vstav3` .

```xml
<addIn>
  <entryPointsCollection>
    <entryPoints>
      <entryPoint>
      </entryPoint>
    </entryPoints>
  </entryPointsCollection>
  <update></update>
  <postActions>
    <postAction>
      <postActionData>
      </postActionData>
    <postAction>
  </postActions>
  <application>
    <customizations>
      <customization>
      </customization>
    </customizations>
  </application
</addIn>
```

|Elemento|Descripción|Atributos|
|-------------|-----------------|----------------|
|[&#60;elemento&#62; customHostSpecified &#40;desarrollo de Office en Visual Studio&#41;](../vsto/customhostspecified-element-office-development-in-visual-studio.md)|Necesario. Marca el manifiesto de manera específica como solución de Office.|None|
|[&#60;elemento&#62; AddIn &#40;desarrollo de Office en Visual Studio&#41;](../vsto/addin-element-office-development-in-visual-studio.md)|Necesario. Almacena los puntos de entrada en un espacio de nombres único.|None|
|[&#60;elemento&#62; entryPointsCollection &#40;desarrollo de Office en Visual Studio&#41;](../vsto/entrypointscollection-element-office-development-in-visual-studio.md)|Necesario. Agrupa todos los ensamblados para una o más soluciones de Office.|**id**|
|[&#60;elemento&#62; entryPoints &#40;desarrollo de Office en Visual Studio&#41;](../vsto/entrypoints-element-office-development-in-visual-studio.md)|Necesario. Agrupa todos los ensamblados para ejecutar una solución de Office.|None|
|[&#60;elemento&#62; entryPoint &#40;desarrollo de Office en Visual Studio&#41;](../vsto/entrypoint-element-office-development-in-visual-studio.md)|Necesario. Identifica el ensamblado para ejecutarlo en una solución de Office.|**class**<br /><br /> **DataContract**|
|[&#60;actualizar el elemento&#62; &#40;el desarrollo de Office en Visual Studio&#41;](../vsto/update-element-office-development-in-visual-studio.md)|Necesario. Configura las actualizaciones para la solución.|**enabled**<br /><br /> **expiration**|
|[&#60;las acciones de&#62; de elementos &#40;desarrollo de Office en Visual Studio&#41;](../vsto/postactions-element-office-development-in-visual-studio.md)|Opcional. Agrupa todas las acciones posteriores a la implementación, que se ejecutan tras la instalación de las soluciones de Office.|None|
|[&#60;elemento&#62; postaction &#40;desarrollo de Office en Visual Studio&#41;](../vsto/postaction-element-office-development-in-visual-studio.md)|Opcional. Identifica una acción posteriores a la implementación.|None|
|[&#60;elemento&#62; postActionData &#40;desarrollo de Office en Visual Studio&#41;](../vsto/postactiondata-element-office-development-in-visual-studio.md)|Opcional. Configura los datos para una acción posterior a la implementación.|None|
|[&#60;elemento&#62; de la aplicación &#40;desarrollo de Office en Visual Studio&#41;](../vsto/application-element-office-development-in-visual-studio.md)|Necesario. Ajusta la información específica de la aplicación en un solo nodo.|None|
|[&#60;personalizaciones&#62; elemento &#40;el desarrollo de Office en Visual Studio&#41;](../vsto/customizations-element-office-development-in-visual-studio.md)|Necesario. Almacena toda la información específica de host de aplicación en un espacio de nombres independiente.|None|
|[ Elemento&#62; de personalización de&#60;&#40;desarrollo de Office en Visual Studio&#41;](../vsto/customization-element-office-development-in-visual-studio.md)|Necesario. Almacena la información específica de host de aplicación en un espacio de nombres independiente.|**xmlns**|
|[&#60;el elemento&#62; de documento &#40;el desarrollo de Office en Visual Studio&#41;](../vsto/document-element-office-development-in-visual-studio.md)|Solo necesario para soluciones de nivel de documento. Almacena información específica de la personalización.|**solutionId**|
|[&#60;elemento&#62; appAddin &#40;desarrollo de Office en Visual Studio&#41;](../vsto/appaddin-element-office-development-in-visual-studio.md)|Solo necesario para soluciones de nivel de aplicación. Almacena información específica de la personalización.|**application**<br /><br /> **loadBehavior**<br /><br /> **keyName**|
|[&#60;friendlyName&#62; elemento &#40;el desarrollo de Office en Visual Studio&#41;](../vsto/friendlyname-element-office-development-in-visual-studio.md)|Opcional. Almacena el nombre del complemento de VSTO que aparece en la lista de complementos instalados de VSTO.|None|
|[&#60;Descripción&#62; elemento &#40;desarrollo de Office en Visual Studio&#41;](../vsto/description-element-office-development-in-visual-studio.md)|Solo es necesario para los complementos de VSTO. Almacena la descripción que aparece en la lista de programas instalados.|None|
|[&#60;elemento de&#62; formRegions &#40;el desarrollo de Office en Visual Studio&#41;](../vsto/formregions-element-office-development-in-visual-studio.md)|Solo es obligatorio para los complementos de VSTO de Outlook que incluyan áreas del formulario.|None|
|[&#60;elemento&#62; formRegion &#40;desarrollo de Office en Visual Studio&#41;](../vsto/formregion-element-office-development-in-visual-studio.md)|Solo es obligatorio para los complementos de VSTO de Outlook que incluyan áreas del formulario.|**Nombre**|
|[&#60;elemento&#62; vstoRuntime &#40;desarrollo de Office en Visual Studio&#41;](../vsto/vstoruntime-element-office-development-in-visual-studio.md)|Necesario. Describe una versión específica del tiempo de ejecución de Visual Studio Tools para Office admitida con la solución de Office.|**emisión**<br /><br /> **version**<br /><br /> **supportUrl**|

## <a name="remarks"></a>Notas
 Puede editar manualmente manifiestos de implementación y aplicación en soluciones de Office. Después, debe volver a firmar la aplicación y los manifiestos de implementación mediante el Herramienta de generación y edición de manifiestos (*mage.exe* y *mageui.exe*). Para obtener más información, vea [Cómo: volver a firmar manifiestos de aplicación y de implementación](../deployment/how-to-re-sign-application-and-deployment-manifests.md).

## <a name="file-location"></a>Ubicación del archivo
 Un manifiesto de aplicación es específico de una versión única de una solución. Por este motivo, los manifiestos de aplicación deben almacenarse por separado de los manifiestos de implementación. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] coloca los archivos específicos de la versión en un subdirectorio con el nombre de la versión asociada en el subdirectorio *archivos de aplicación* de la carpeta de publicación.

## <a name="file-name-syntax"></a>Sintaxis de los nombres de archivo
 El nombre de un archivo de manifiesto de aplicación debe ser el nombre completo y la extensión de la aplicación, tal como se identifica en el elemento **assemblyIdentity** , seguido de la extensión *. manifest*. Por ejemplo, un manifiesto de aplicación que hace referencia a la personalización de *OutlookAddIn1.dll* usaría la siguiente sintaxis de nombre de archivo.

 `OutlookAddIn1.dll.manifest`

## <a name="see-also"></a>Vea también

- [Manifiestos de implementación para soluciones de Office](../vsto/deployment-manifests-for-office-solutions.md)
- [Manifiesto de aplicación ClickOnce](../deployment/clickonce-application-manifest.md)