---
title: "Cómo: Solucionar problemas de plantillas | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Visual Studio templates, troubleshooting
ms.assetid: 3e577ad2-f725-4c11-93b3-477f2404ec81
caps.latest.revision: "10"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: af00efbeb759bfc41d12e0ab814ecadd4bbc7799
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-troubleshoot-templates"></a>Cómo: Solucionar problemas de plantillas
Si una plantilla no se puede cargar en el entorno de desarrollo, hay varias maneras de localizar la causa del problema.  
  
## <a name="validating-the-vstemplate-file"></a>Validar el archivo .vstemplate  
 Si el archivo .vstemplate en una plantilla no cumple el esquema de plantilla de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], la plantilla podría no aparecer en el cuadro de diálogo **Nuevo proyecto**.  
  
#### <a name="to-validate-the-vstemplate-file"></a>Para validar el archivo .vstemplate  
  
1.  Busque el archivo .zip que contiene la plantilla.  
  
2.  Extraiga el archivo .zip.  
  
3.  En el menú **Archivo** en [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], haga clic en **Abrir** y en **Archivo**.  
  
4.  Seleccione el archivo .vstemplate para la plantilla y haga clic en **Abrir**.  
  
5.  Compruebe que el XML del archivo .vstemplate cumple el esquema de plantilla de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Para obtener más información sobre el esquema .vstemplate, vea [Visual Studio Template Schema Reference](../extensibility/visual-studio-template-schema-reference.md) (Referencia de esquema de plantillas de Visual Studio).  
  
    > [!NOTE]
    >  Para obtener compatibilidad con IntelliSense mientras se crea el archivo .vstemplate, agregue un atributo `xmlns` al elemento `VSTemplate` y asígnele un valor de http://schemas.microsoft.com/developer/vstemplate/2005.  
  
6.  Guarde y cierre el archivo .vstemplate.  
  
7.  Seleccione los archivos incluidos en la plantilla, haga clic con el botón derecho, seleccione **Enviar a** y haga clic en **Carpeta comprimida (en zip)**. Los archivos seleccionados se comprimen en un archivo .zip.  
  
8.  Coloque el nuevo archivo .zip en el mismo directorio que el antiguo.  
  
9. Elimine los archivos de plantilla extraídos y el archivo .zip de plantilla antiguo.  
  
## <a name="monitoring-the-event-log"></a>Supervisar el registro de eventos  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] registra los errores que se detectan al procesar archivos .zip de plantilla. Si una plantilla no aparece en el cuadro de diálogo **Nuevo proyecto** según lo previsto, puede usar el **Visor de eventos** para solucionar el problema.  
  
#### <a name="to-locate-template-errors-in-event-viewer"></a>Para buscar errores de plantilla en el Visor de eventos  
  
1.  En Windows, haga clic en **Inicio** y en **Panel de control**, haga doble clic en **Herramientas administrativas** y, después, de nuevo doble clic en **Visor de eventos**.  
  
2.  En el panel izquierdo, haga clic en **Aplicación**.  
  
3.  Busque los eventos que tengan un valor **Source** de `Visual Studio - VsTemplate`.  
  
4.  Haga doble clic en un evento de plantilla para ver el error.  
  
## <a name="see-also"></a>Vea también  
 [Personalizar plantillas](../ide/customizing-project-and-item-templates.md)   
 [Crear plantillas para proyectos y elementos en Visual Studio](../ide/creating-project-and-item-templates.md)   
 [Referencia de esquema de plantillas de Visual Studio](../extensibility/visual-studio-template-schema-reference.md)