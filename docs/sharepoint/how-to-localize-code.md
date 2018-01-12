---
title: "Cómo: localizar código | Documentos de Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- localizing code [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, localizing
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 95c029a7a90283314bdded2a6beeb7f023d7e827
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-localize-code"></a>Cómo: Localizar código
  El código sin localizar usa valores de cadena codificados de forma rígida. Para localizar cadenas de código, sustitúyalas por llamadas a <xref:System.Web.HttpContext.GetGlobalResourceObject%2A>, que es un método que hace referencia a los recursos localizados.  
  
## <a name="localizing-code"></a>Adaptar código  
  
#### <a name="to-localize-code"></a>Para localizar el código  
  
1.  En **el Explorador de soluciones**, abra el menú contextual de un elemento de proyecto y, a continuación, elija **agregar**, **módulo**.  
  
     Elija la **archivo de recursos** plantilla.  
  
    > [!NOTE]  
    >  Asegúrese de agregar el archivo de recursos a un elemento de proyecto de SharePoint para que esté disponible la propiedad Tipo de implementación. Esta propiedad es necesaria más adelante en este procedimiento.  
  
2.  Asigne al archivo de recursos del idioma predeterminado el nombre que desee y agréguele la extensión .resx, por ejemplo, MyAppResources.resx.  
  
3.  Repita los pasos 1 y 2 para agregar archivos de recursos independientes al elemento de proyecto de SharePoint: uno para cada idioma localizado.  
  
     Use el mismo nombre base para cada archivo de recursos localizado, pero agregue el identificador de la referencia cultural. Por ejemplo, el nombre del archivo de recursos localizado en alemán será MyAppResources.de-DE.resx.  
  
4.  Abra cada uno de los archivos de recursos y agregue las cadenas localizadas. Use los mismos identificadores de cadena en cada archivo.  
  
5.  Cambie el valor de la **tipo de implementación** propiedad de cada archivo de recursos para **AppGlobalResource** para hacer que cada archivo que se va a implementar en la carpeta App_GlobalResources del servidor.  
  
6.  Deje el valor de la **acción de compilación** propiedad de cada archivo como **recurso incrustado**.  
  
     Los recursos incrustados se compilan en el archivo DLL del proyecto.  
  
7.  Compile el proyecto para crear los archivos DLL satélite de recursos.  
  
8.  En el **Diseñador de paquetes**, elija la **avanzadas** ficha y, a continuación, agregue el ensamblado satélite.  
  
9. En el **ubicación** cuadro, anteponga a una carpeta de identificador de referencia cultural y la ruta de acceso de ubicación, por ejemplo de-DE\\*el nombre del elemento de proyecto*. resources.dll.  
  
10. Si la solución aún no hace referencia el ensamblado System.Web, agregue una referencia y una directiva del código al espacio de nombres <xref:System.Web>.  
  
11. Busque todas las cadenas codificadas de forma rígida en el código visibles para los usuarios, como texto de la interfaz de usuario, errores y texto del mensaje. Reemplácelas por una llamada al método <xref:System.Web.HttpContext.GetGlobalResourceObject%2A> utilizando la sintaxis siguiente:  
  
    ```  
    HttpContext.GetGlobalResourceObject("Resource File Name", "String ID")  
    ```  
  
12. Elija la tecla F5 para compilar y ejecutar la aplicación.  
  
13. En SharePoint, cambie el idioma de presentación predeterminado.  
  
     Las cadenas localizadas aparecen en la aplicación. Para mostrar los recursos localizados, el servidor de SharePoint debe tener instalado el paquete de idioma que coincide con la referencia cultural del archivo de recursos.  
  
## <a name="see-also"></a>Vea también  
 [Localizar soluciones de SharePoint](../sharepoint/localizing-sharepoint-solutions.md)   
 [Cómo: localizar una característica](../sharepoint/how-to-localize-a-feature.md)   
 [Cómo: localizar el marcado ASPX](../sharepoint/how-to-localize-aspx-markup.md)   
 [Cómo: Agregar un archivo de recursos](../sharepoint/how-to-add-a-resource-file.md)  
  
  