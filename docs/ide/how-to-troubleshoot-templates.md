---
title: "C&#243;mo: Solucionar problemas de plantillas | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "plantillas de Visual Studio, solucionar problemas"
ms.assetid: 3e577ad2-f725-4c11-93b3-477f2404ec81
caps.latest.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 10
---
# C&#243;mo: Solucionar problemas de plantillas
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Si una plantilla no se carga en el entorno de desarrollo, hay varias maneras de localizar el problema.  
  
## Validar el archivo .vstemplate  
 Si el archivo .vstemplate de una plantilla no cumple el esquema de plantillas de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], es posible que la plantilla no aparezca en el cuadro de diálogo **Nuevo proyecto**.  
  
#### Para validar el archivo .vstemplate  
  
1.  Busque el archivo .zip que contiene la plantilla.  
  
2.  Extraiga el archivo . zip.  
  
3.  En el menú **Archivo** de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], haga clic en **Abrir** y, a continuación, en **Archivo**.  
  
4.  Seleccione el archivo .vstemplate de la plantilla y haga clic en **Abrir**.  
  
5.  Compruebe que el código XML del archivo .vstemplate cumpla el esquema de plantilla de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  Para obtener más información sobre el esquema de .vstemplate, vea [Referencia de esquema de plantillas de Visual Studio](../extensibility/visual-studio-template-schema-reference.md).  
  
    > [!NOTE]
    >  Para obtener compatibilidad con IntelliSense al crear el archivo .vstemplate, agregue un atributo `xmlns` al elemento `VSTemplate` y asígnele un valor de http:\/\/schemas.microsoft.com\/developer\/vstemplate\/2005.  
  
6.  Guarde y cierre el archivo .vstemplate.  
  
7.  Seleccione los archivos incluidos en la plantilla, haga clic con el botón secundario del mouse, seleccione **Enviar a** y haga clic en **Carpeta comprimida \(en zip\)**.  Los archivos seleccionados se comprimen en un archivo .zip.  
  
8.  Coloque el nuevo archivo .zip en el mismo directorio que el archivo .zip anterior.  
  
9. Elimine los archivos de plantilla extraídos y el archivo .zip de plantilla antiguo.  
  
## Supervisar el registro de eventos  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] registra los errores que surgen al procesar archivos de plantilla .zip.  Si una plantilla no aparece en el cuadro de diálogo **Nuevo proyecto** según lo esperado, puede utilizar el **Visor de eventos** para solucionar el problema.  
  
#### Para buscar los errores de la plantilla en el Visor de eventos  
  
1.  En Windows, haga clic en **Inicio** y en **Panel de control**, haga doble clic en **Herramientas administrativas** y, a continuación, de nuevo doble clic en **Visor de eventos**.  
  
2.  En el panel izquierdo, haga clic en **Aplicación**.  
  
3.  Busque eventos cuyo valor de **Origen** sea `Visual Studio - VsTemplate`.  
  
4.  Haga doble clic en un evento de plantilla para ver el error.  
  
## Vea también  
 [Personalizar plantillas](../ide/customizing-project-and-item-templates.md)   
 [Crear plantillas de proyecto y de elemento personalizadas](../ide/creating-project-and-item-templates.md)   
 [Referencia de esquema de plantillas de Visual Studio](../extensibility/visual-studio-template-schema-reference.md)