---
title: "Manifiestos de aplicaci&#243;n para soluciones de Office"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "manifiestos de aplicación [desarrollo de Office en Visual Studio]"
ms.assetid: dd38685f-f429-4a35-8c11-a03372c9770a
caps.latest.revision: 41
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 40
---
# Manifiestos de aplicaci&#243;n para soluciones de Office
  Un manifiesto de aplicación es un archivo XML que describe los ensamblados que se cargan en una solución de Microsoft Office. Las herramientas de desarrollo de Microsoft Office en Visual Studio usan el esquema del manifiesto de aplicación [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] definido en la referencia [Manifiesto de aplicación ClickOnce](../deployment/clickonce-application-manifest.md).  
  
 Los manifiestos de aplicación para soluciones de Office usan los siguientes elementos y atributos [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)].  
  
|Elemento|Descripción|Atributos|  
|--------------|-----------------|---------------|  
|[&#60;assembly&#62; &#40;Elemento&#41;](~/deployment/assembly-element-clickonce-application.md)|Requerido. Elemento de nivel superior.|`manifestVersion`|  
|[Elemento &#60;assemblyIdentity&#62; &#40;Aplicación ClickOnce&#41;](~/deployment/assemblyidentity-element-clickonce-application.md)|Obligatorio. Identifica el ensamblado principal de la aplicación [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)].|`name`<br /><br /> `version`<br /><br /> `publicKeyToken`<br /><br /> `processorArchitecture`<br /><br /> `language`|  
|[&#60;trustInfo&#62; &#40;Elemento&#41;](~/deployment/trustinfo-element-clickonce-application.md)|Identifica los requisitos de seguridad de la aplicación.|Ninguno|  
|[Elemento &#60;entryPoint&#62; &#40;Aplicación ClickOnce&#41;](~/deployment/entrypoint-element-clickonce-application.md)|Obligatorio. Identifica el punto de entrada del código de aplicación para la ejecución.|`name`<br /><br /> `dependencyName`<br /><br /> `customHostSpecified`|  
|[Elemento &#60;dependency&#62; &#40;Aplicación ClickOnce&#41;](~/deployment/dependency-element-clickonce-application.md)|Obligatorio. Identifica cada dependencia necesaria para que se ejecute la aplicación. Identifica opcionalmente los ensamblados que se tienen que preinstalar.|Ninguno|  
|[Elemento &#60;file&#62; &#40;Aplicación ClickOnce&#41;](~/deployment/file-element-clickonce-application.md)|Obligatorio. Identifica cada archivo que no es de ensamblado y que se usa por la aplicación. Puede incluir datos de aislamiento del modelo de objetos componentes \(COM\) asociados al archivo.|`name`<br /><br /> `size`|  
  
 Los manifiestos de aplicación para soluciones de Office tienen el siguiente elemento en el espacio de nombres `co.v1`.  
  
```  
<entryPoint> <co.v1:customHostSpecified /> </entryPoint>   
```  
  
 Estos manifiestos de aplicación también tienen los siguientes elementos y atributos en el espacio de nombres `vstav3`.  
  
```  
<addIn> <entryPointsCollection> <entryPoints> <entryPoint> </entryPoint> </entryPoints> </entryPointsCollection> <update></update> <postActions> <postAction> <postActionData> </postActionData> <postAction> </postActions> <application> <customizations> <customization> </customization> </customizations> </application </addIn>  
```  
  
|Elemento|Descripción|Atributos|  
|--------------|-----------------|---------------|  
|[Elemento &#60;customHostSpecified&#62; &#40;desarrollo de Office en Visual Studio&#41;](../vsto/customhostspecified-element-office-development-in-visual-studio.md)|Obligatorio. Marca el manifiesto de manera específica como solución de Office.|Ninguna|  
|[Elemento &#60;addin&#62; &#40;desarrollo de Office en Visual Studio&#41;](../vsto/addin-element-office-development-in-visual-studio.md)|Obligatorio. Almacena los puntos de entrada en un espacio de nombres único.|Ninguna|  
|[&#60;entryPointsCollection&#62; &#40;elemento, Desarrollo de Office en Visual Studio&#41;](../vsto/entrypointscollection-element-office-development-in-visual-studio.md)|Obligatorio. Agrupa todos los ensamblados para una o más soluciones de Office.|`id`|  
|[&#60;entryPoints&#62; &#40;elemento, Desarrollo de Office en Visual Studio&#41;](../vsto/entrypoints-element-office-development-in-visual-studio.md)|Obligatorio. Agrupa todos los ensamblados para ejecutar una solución de Office.|Ninguna|  
|[Elemento &#60;entryPoint&#62; &#40;desarrollo de Office en Visual Studio&#41;](../vsto/entrypoint-element-office-development-in-visual-studio.md)|Obligatorio. Identifica el ensamblado para ejecutarlo en una solución de Office.|`class`<br /><br /> `contract`|  
|[Elemento &#60;update&#62; &#40;desarrollo de Office en Visual Studio&#41;](../vsto/update-element-office-development-in-visual-studio.md)|Obligatorio. Configura las actualizaciones para la solución.|`enabled`<br /><br /> `expiration`|  
|[Elemento &#60;postActions&#62; &#40;desarrollo de Office en Visual Studio&#41;](../vsto/postactions-element-office-development-in-visual-studio.md)|Opcional. Agrupa todas las acciones posteriores a la implementación, que se ejecutan tras la instalación de las soluciones de Office.|Ninguna|  
|[Elemento &#60;postAction&#62; &#40;desarrollo de Office en Visual Studio&#41;](../vsto/postaction-element-office-development-in-visual-studio.md)|Opcional. Identifica una acción posteriores a la implementación.|Ninguno|  
|[Elemento &#60;postActionData&#62; &#40;desarrollo de Office en Visual Studio&#41;](../vsto/postactiondata-element-office-development-in-visual-studio.md)|Opcional. Configura los datos para una acción posterior a la implementación.|Ninguno|  
|[Elemento &#60;application&#62; &#40;desarrollo de Office en Visual Studio&#41;](../vsto/application-element-office-development-in-visual-studio.md)|Obligatorio. Ajusta la información específica de la aplicación en un solo nodo.|Ninguna|  
|[&#60;customizations&#62; &#40;elemento, Desarrollo de Office en Visual Studio&#41;](../vsto/customizations-element-office-development-in-visual-studio.md)|Obligatorio. Almacena toda la información específica de host de aplicación en un espacio de nombres independiente.|Ninguna|  
|[Elemento &#60;customization&#62; &#40;desarrollo de Office en Visual Studio&#41;](../vsto/customization-element-office-development-in-visual-studio.md)|Obligatorio. Almacena la información específica de host de aplicación en un espacio de nombres independiente.|`xmlns`|  
|[Elemento &#60;document&#62; &#40;desarrollo de Office en Visual Studio&#41;](../vsto/document-element-office-development-in-visual-studio.md)|Solo necesario para soluciones de nivel de documento. Almacena información específica de la personalización.|`solutionId`|  
|[Elemento &#60;appAddin&#62; &#40;desarrollo de Office en Visual Studio&#41;](../vsto/appaddin-element-office-development-in-visual-studio.md)|Solo necesario para soluciones de nivel de aplicación. Almacena información específica de la personalización.|`application`<br /><br /> `loadBehavior`<br /><br /> `keyName`|  
|[&#60;friendlyName&#62; &#40;elemento&#41; &#40;desarrollo de Office en Visual Studio&#41;](../vsto/friendlyname-element-office-development-in-visual-studio.md)|Opcional. Almacena el nombre del complemento de VSTO que aparece en la lista de complementos instalados de VSTO.|Ninguna|  
|[Elemento &#60;description&#62; &#40;desarrollo de Office en Visual Studio&#41;](../vsto/description-element-office-development-in-visual-studio.md)|Solo necesario para complementos de VSTO. Almacena la descripción que aparece en la lista de programas instalados.|Ninguno|  
|[Elemento &#60;formRegions&#62; &#40;desarrollo de Office en Visual Studio&#41;](../vsto/formregions-element-office-development-in-visual-studio.md)|Solo es obligatorio para los complementos de VSTO de Outlook que incluyan áreas del formulario.|Ninguna|  
|[Elemento &#60;formRegion&#62; &#40;desarrollo de Office en Visual Studio&#41;](../vsto/formregion-element-office-development-in-visual-studio.md)|Solo es obligatorio para los complementos de VSTO de Outlook que incluyan áreas del formulario.|`Name`|  
|[Elemento &#60;vstoRuntime&#62; &#40;desarrollo de Office en Visual Studio&#41;](../vsto/vstoruntime-element-office-development-in-visual-studio.md)|Obligatorio. Describe una versión específica del tiempo de ejecución de Visual Studio Tools para Office admitida con la solución de Office.|`release`<br /><br /> `version`<br /><br /> `supportUrl`|  
  
## Comentarios  
 Puede editar manualmente manifiestos de implementación y aplicación en soluciones de Office. Después, debe volver a firmar la aplicación y los manifiestos de implementación mediante la generación de manifiestos y la herramienta de edición \(mage.exe y mageui.exe\). Para obtener más información, consulta [Cómo: Volver a firmar manifiestos de aplicación e implementación](~/deployment/how-to-re-sign-application-and-deployment-manifests.md).  
  
## Ubicación del archivo  
 Un manifiesto de aplicación es específico de una versión única de una solución. Por este motivo, los manifiestos de aplicación deben almacenarse por separado de los manifiestos de implementación.[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] coloca los archivos específicos de la versión en un subdirectorio con nombre tras la versión asociada del subdirectorio **Archivos de aplicación** de la carpeta de publicación.  
  
## Sintaxis de los nombres de archivo  
 El nombre de un archivo de manifiesto de aplicación debe ser el nombre completo y la extensión de la aplicación según se identifica en el elemento `assemblyIdentity`, seguido del .manifest de extensión. Por ejemplo, un manifiesto de aplicación que hace referencia a la personalización de OutlookAddIn1.dll usaría la siguiente sintaxis de nombre de archivo.  
  
 `OutlookAddIn1.dll.manifest`  
  
## Vea también  
 [Manifiestos de implementación para soluciones de Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [Manifiesto de aplicación ClickOnce](../deployment/clickonce-application-manifest.md)  
  
  