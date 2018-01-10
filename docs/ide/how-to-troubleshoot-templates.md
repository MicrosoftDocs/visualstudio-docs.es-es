---
title: "Cómo: Solucionar problemas de plantillas en Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: templates [Visual Studio], troubleshooting
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 1d78554f39be1fdf21c5bbcb4d0abf5cf691fce9
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-troubleshoot-templates"></a>Cómo: Solucionar problemas de plantillas

Si una plantilla no se puede cargar en el entorno de desarrollo, hay varias maneras de localizar la causa del problema.

## <a name="validating-the-vstemplate-file"></a>Validación del archivo .vstemplate

Si el archivo .vstemplate en una plantilla no cumple el esquema de plantilla de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], la plantilla podría no aparecer en el cuadro de diálogo **Nuevo proyecto**.

### <a name="to-validate-the-vstemplate-file"></a>Para validar el archivo .vstemplate

1.  Busque el archivo .zip que contiene la plantilla.  

2.  Extraiga el archivo .zip.  

3.  En el menú **Archivo** en [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], haga clic en **Abrir** y en **Archivo**.

4.  Seleccione el archivo .vstemplate para la plantilla y haga clic en **Abrir**.  
  
5.  Compruebe que el XML del archivo .vstemplate cumple el esquema de plantilla de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Para obtener más información sobre el esquema .vstemplate, vea [Visual Studio Template Schema Reference](../extensibility/visual-studio-template-schema-reference.md) (Referencia de esquema de plantillas de Visual Studio).  

    > [!NOTE]
    > Para obtener compatibilidad con IntelliSense mientras se crea el archivo .vstemplate, agregue un atributo `xmlns` al elemento `VSTemplate` y asígnele un valor de http://schemas.microsoft.com/developer/vstemplate/2005.

6.  Guarde y cierre el archivo .vstemplate.  
  
7.  Seleccione los archivos incluidos en la plantilla, haga clic con el botón derecho, seleccione **Enviar a** y haga clic en **Carpeta comprimida (en zip)**. Los archivos seleccionados se comprimen en un archivo .zip.  
  
8.  Coloque el nuevo archivo .zip en el mismo directorio que el antiguo.  
  
9. Elimine los archivos de plantilla extraídos y el archivo .zip de plantilla antiguo.

## <a name="monitoring-the-event-log"></a>Supervisar el registro de eventos

[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] registra los errores que se detectan al procesar archivos .zip de plantilla. Si una plantilla no aparece en el cuadro de diálogo **Nuevo proyecto** según lo previsto, puede usar el **Visor de eventos** para solucionar el problema.

### <a name="to-locate-template-errors-in-event-viewer"></a>Para buscar errores de plantilla en el Visor de eventos

1.  En Windows, haga clic en **Inicio** y en **Panel de control**, haga doble clic en **Herramientas administrativas** y, después, de nuevo doble clic en **Visor de eventos**.  
  
2.  En el panel izquierdo, haga clic en **Aplicación**.  
  
3.  Busque los eventos que tengan un valor **Source** de `Visual Studio - VsTemplate`.  
  
4.  Haga doble clic en un evento de plantilla para ver el error.

## <a name="see-also"></a>Vea también

[Personalizar plantillas](../ide/customizing-project-and-item-templates.md)   
[Crear plantillas para proyectos y elementos en Visual Studio](../ide/creating-project-and-item-templates.md)   
[Referencia de esquema de plantillas de Visual Studio](../extensibility/visual-studio-template-schema-reference.md)