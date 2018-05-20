---
title: Manifiestos de aplicación para soluciones de Office
ms.custom: ''
ms.date: 02/02/2017
ms.technology: office-development
ms.prod: visual-studio-dev15
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 622d2066f6acfe1fdf344f06ee5bbbbdf3d9b410
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/17/2018
---
# <a name="application-manifests-for-office-solutions"></a>Manifiestos de aplicación para soluciones de Office
  Un manifiesto de aplicación es un archivo XML que describe los ensamblados que se cargan en una solución de Microsoft Office. Usan las herramientas de desarrollo de Microsoft Office en Visual Studio la [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] esquema del manifiesto de aplicación definido en el [manifiesto de aplicación ClickOnce](/visualstudio/deployment/clickonce-application-manifest) referencia.  
  
 Los manifiestos de aplicación para soluciones de Office usan los siguientes elementos y atributos [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] .  
  
|Elemento|Descripción|Atributos|  
|-------------|-----------------|----------------|  
|[&#60;ensamblado&#62; elemento &#40;aplicación ClickOnce&#41;](/visualstudio/deployment/assembly-element-clickonce-deployment)|Requerido. Elemento de nivel superior.|**ManifestVersion**|  
|[&#60;assemblyIdentity&#62; elemento &#40;aplicación ClickOnce&#41;](/visualstudio/deployment/assemblyidentity-element-clickonce-deployment)|Requerido. Identifica el ensamblado principal de la aplicación [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] .|**name**<br /><br /> **version**<br /><br /> **PublicKeyToken**<br /><br /> **ProcessorArchitecture**<br /><br /> **language**|  
|[&#60;trustInfo&#62; elemento &#40;aplicación ClickOnce&#41;](/visualstudio/deployment/trustinfo-element-clickonce-application)|Identifica los requisitos de seguridad de la aplicación.|Ninguna|  
|[&#60;punto de entrada&#62; elemento &#40;aplicación ClickOnce&#41;](/visualstudio/deployment/entrypoint-element-clickonce-application)|Requerido. Identifica el punto de entrada del código de aplicación para la ejecución.|**name**<br /><br /> **dependencyName**<br /><br /> **customHostSpecified**|  
|[&#60;dependencia&#62; elemento &#40;aplicación ClickOnce&#41;](/visualstudio/deployment/dependency-element-clickonce-deployment)|Requerido. Identifica cada dependencia necesaria para que se ejecute la aplicación. Identifica opcionalmente los ensamblados que se tienen que preinstalar.|Ninguna|  
|[&#60;archivo&#62; elemento &#40;aplicación ClickOnce&#41;](/visualstudio/deployment/file-element-clickonce-application)|Requerido. Identifica cada archivo que no es de ensamblado y que se usa por la aplicación. Puede incluir datos de aislamiento del modelo de objetos componentes (COM) asociados al archivo.|**name**<br /><br /> **size**|  
  
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
|[&#60;customHostSpecified&#62; elemento &#40;desarrollo de Office en Visual Studio&#41;](../vsto/customhostspecified-element-office-development-in-visual-studio.md)|Requerido. Marca el manifiesto de manera específica como solución de Office.|Ninguna|  
|[&#60;complemento&#62; elemento &#40;desarrollo de Office en Visual Studio&#41;](../vsto/addin-element-office-development-in-visual-studio.md)|Requerido. Almacena los puntos de entrada en un espacio de nombres único.|Ninguna|  
|[&#60;entryPointsCollection&#62; elemento &#40;desarrollo de Office en Visual Studio&#41;](../vsto/entrypointscollection-element-office-development-in-visual-studio.md)|Requerido. Agrupa todos los ensamblados para una o más soluciones de Office.|**identificador**|  
|[&#60;entryPoints&#62; elemento &#40;desarrollo de Office en Visual Studio&#41;](../vsto/entrypoints-element-office-development-in-visual-studio.md)|Requerido. Agrupa todos los ensamblados para ejecutar una solución de Office.|Ninguna|  
|[&#60;punto de entrada&#62; elemento &#40;desarrollo de Office en Visual Studio&#41;](../vsto/entrypoint-element-office-development-in-visual-studio.md)|Requerido. Identifica el ensamblado para ejecutarlo en una solución de Office.|**class**<br /><br /> **Contrato**|  
|[&#60;actualizar&#62; elemento &#40;desarrollo de Office en Visual Studio&#41;](../vsto/update-element-office-development-in-visual-studio.md)|Requerido. Configura las actualizaciones para la solución.|**enabled**<br /><br /> **expiración**|  
|[&#60;postActions&#62; elemento &#40;desarrollo de Office en Visual Studio&#41;](../vsto/postactions-element-office-development-in-visual-studio.md)|Opcional. Agrupa todas las acciones posteriores a la implementación, que se ejecutan tras la instalación de las soluciones de Office.|Ninguna|  
|[&#60;postAction&#62; elemento &#40;desarrollo de Office en Visual Studio&#41;](../vsto/postaction-element-office-development-in-visual-studio.md)|Opcional. Identifica una acción posteriores a la implementación.|Ninguna|  
|[&#60;postActionData&#62; elemento &#40;desarrollo de Office en Visual Studio&#41;](../vsto/postactiondata-element-office-development-in-visual-studio.md)|Opcional. Configura los datos para una acción posterior a la implementación.|Ninguna|  
|[&#60;aplicación&#62; elemento &#40;desarrollo de Office en Visual Studio&#41;](../vsto/application-element-office-development-in-visual-studio.md)|Requerido. Ajusta la información específica de la aplicación en un solo nodo.|Ninguna|  
|[&#60;las personalizaciones&#62; elemento &#40;desarrollo de Office en Visual Studio&#41;](../vsto/customizations-element-office-development-in-visual-studio.md)|Requerido. Almacena toda la información específica de host de aplicación en un espacio de nombres independiente.|Ninguna|  
|[&#60;personalización&#62; elemento &#40;desarrollo de Office en Visual Studio&#41;](../vsto/customization-element-office-development-in-visual-studio.md)|Requerido. Almacena la información específica de host de aplicación en un espacio de nombres independiente.|**xmlns**|  
|[&#60;documento&#62; elemento &#40;desarrollo de Office en Visual Studio&#41;](../vsto/document-element-office-development-in-visual-studio.md)|Solo necesario para soluciones de nivel de documento. Almacena información específica de la personalización.|**solutionId**|  
|[&#60;appAddin&#62; elemento &#40;desarrollo de Office en Visual Studio&#41;](../vsto/appaddin-element-office-development-in-visual-studio.md)|Solo necesario para soluciones de nivel de aplicación. Almacena información específica de la personalización.|**Aplicación**<br /><br /> **loadBehavior**<br /><br /> **keyName**|  
|[&#60;friendlyName&#62; elemento &#40;desarrollo de Office en Visual Studio&#41;](../vsto/friendlyname-element-office-development-in-visual-studio.md)|Opcional. Almacena el nombre del complemento de VSTO que aparece en la lista de complementos instalados de VSTO.|Ninguna|  
|[&#60;descripción&#62; elemento &#40;desarrollo de Office en Visual Studio&#41;](../vsto/description-element-office-development-in-visual-studio.md)|Solo necesario para complementos de VSTO. Almacena la descripción que aparece en la lista de programas instalados.|Ninguna|  
|[&#60;formRegions&#62; elemento &#40;desarrollo de Office en Visual Studio&#41;](../vsto/formregions-element-office-development-in-visual-studio.md)|Solo es obligatorio para los complementos de VSTO de Outlook que incluyan áreas del formulario.|Ninguna|  
|[&#60;formRegion&#62; elemento &#40;desarrollo de Office en Visual Studio&#41;](../vsto/formregion-element-office-development-in-visual-studio.md)|Solo es obligatorio para los complementos de VSTO de Outlook que incluyan áreas del formulario.|**Name**|  
|[&#60;vstoRuntime&#62; elemento &#40;desarrollo de Office en Visual Studio&#41;](../vsto/vstoruntime-element-office-development-in-visual-studio.md)|Requerido. Describe una versión específica del tiempo de ejecución de Visual Studio Tools para Office admitida con la solución de Office.|**release**<br /><br /> **version**<br /><br /> **supportUrl**|  
  
## <a name="remarks"></a>Comentarios  
 Puede editar manualmente manifiestos de implementación y aplicación en soluciones de Office. Después, debe volver a firmar la aplicación y los manifiestos de implementación mediante el uso de la herramienta de edición y generación de manifiestos (*mage.exe* y *mageui.exe*). Para obtener más información, consulte [Cómo: volver a firmar los manifiestos de aplicación e implementación](/visualstudio/deployment/how-to-re-sign-application-and-deployment-manifests).  
  
## <a name="file-location"></a>Ubicación del archivo  
 Un manifiesto de aplicación es específico de una versión única de una solución. Por este motivo, los manifiestos de aplicación deben almacenarse por separado de los manifiestos de implementación. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] coloca los archivos específicos de la versión en un subdirectorio con el nombre de la versión asociada de la *archivos de la aplicación* subdirectorio en la carpeta de publicación.  
  
## <a name="file-name-syntax"></a>Sintaxis de nombre de archivo  
 El nombre de un archivo de manifiesto de aplicación debe ser el nombre completo y la extensión de la aplicación según se identifica en el **assemblyIdentity** elemento, seguido del .manifest de extensión. Por ejemplo, un manifiesto de aplicación que hace referencia a la *OutlookAddIn1.dll* personalización utilizaría la siguiente sintaxis de nombre de archivo.  
  
 `OutlookAddIn1.dll.manifest`  
  
## <a name="see-also"></a>Vea también  
 [Manifiestos de implementación para soluciones de Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [Manifiesto de aplicación ClickOnce](/visualstudio/deployment/clickonce-application-manifest)  
  
  