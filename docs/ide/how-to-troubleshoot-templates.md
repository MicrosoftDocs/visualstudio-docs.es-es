---
title: "Solución de problemas de carga de plantillas de proyecto y de elemento de Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 01/02/2018
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: templates [Visual Studio], troubleshooting
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: ba6d9a73cd45a0e497fb2ecc0f4b4697071e3b37
ms.sourcegitcommit: 9357209350167e1eb7e50b483e44893735d90589
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/05/2018
---
# <a name="how-to-troubleshoot-templates"></a>Cómo: Solucionar problemas de plantillas

Si una plantilla no se puede cargar en el entorno de desarrollo, hay varias maneras de localizar la causa del problema.

## <a name="validate-the-vstemplate-file"></a>Validación del archivo .vstemplate

Si el archivo .vstemplate en una plantilla no cumple el esquema de plantilla de Visual Studio, la plantilla podría no aparecer en el cuadro de diálogo **Nuevo proyecto**.

### <a name="to-validate-the-vstemplate-file"></a>Para validar el archivo .vstemplate

1. Busque el archivo .zip que contiene la plantilla.

1. Extraiga el archivo .zip.

1. En el menú **Archivo** de Visual Studio, seleccione **Abrir** > **Archivo**.

1. Seleccione el archivo .vstemplate para la plantilla y seleccione **Abrir**.

1. Compruebe que el XML del archivo .vstemplate cumple el esquema de plantilla. Para obtener más información sobre el esquema .vstemplate, vea [Template Schema Reference](../extensibility/visual-studio-template-schema-reference.md) (Referencia de esquema de plantillas).

    > [!NOTE]
    > Para obtener compatibilidad con IntelliSense mientras se crea el archivo .vstemplate, agregue un atributo `xmlns` al elemento `VSTemplate` y asígnele un valor de http://schemas.microsoft.com/developer/vstemplate/2005.

1. Guarde y cierre el archivo .vstemplate.

1. Seleccione los archivos incluidos en la plantilla, haga clic con el botón derecho y seleccione **Enviar a** > **Carpeta comprimida (en zip)**. Los archivos seleccionados se comprimen en un archivo .zip.

1. Coloque el nuevo archivo .zip en el mismo directorio que el antiguo.

1. Elimine los archivos de plantilla extraídos y el archivo .zip de plantilla antiguo.

## <a name="monitor-the-event-log"></a>Supervisión del registro de eventos

Visual Studio registra los errores que se encuentra al procesar archivos .zip de plantilla. Si una plantilla no aparece en el cuadro de diálogo **Nuevo proyecto** según lo previsto, puede usar el **Visor de eventos** para solucionar el problema.

### <a name="to-locate-template-errors-in-event-viewer"></a>Para buscar errores de plantilla en el Visor de eventos

1. En Windows, en el menú **Inicio**, seleccione **Herramientas administrativas de Windows** > **Visor de eventos**.

1. En el panel izquierdo, seleccione **Registros de Windows** > **Aplicación**.

1. Busque los eventos que tengan un valor **Source** de `Visual Studio - VsTemplate`.

1. Para ver un error, haga doble clic en un evento de plantilla.

## <a name="enable-diagnostic-logging"></a>Habilitación del registro de diagnóstico

Puede habilitar el registro de diagnóstico para la detección de plantillas si sigue los pasos de [Solución de problemas de detección de plantillas (Extensibilidad)](../extensibility/troubleshooting-template-discovery.md).

## <a name="see-also"></a>Vea también

[Solución de problemas de detección de plantillas (Extensibilidad)](../extensibility/troubleshooting-template-discovery.md)  
[Personalización de plantillas](../ide/customizing-project-and-item-templates.md)  
[Crear plantillas para proyectos y elementos](../ide/creating-project-and-item-templates.md)  
[Referencia de esquema de plantillas](../extensibility/visual-studio-template-schema-reference.md)