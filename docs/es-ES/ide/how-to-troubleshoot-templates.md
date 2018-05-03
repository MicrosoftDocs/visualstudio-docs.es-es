---
title: Solución de problemas de carga de plantillas de proyecto y de elemento de Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 01/02/2018
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- templates [Visual Studio], troubleshooting
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: f7e952f8eb445787a2a574ae3431ba6ad8728248
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/19/2018
---
# <a name="how-to-troubleshoot-templates"></a>Cómo: Solucionar problemas de plantillas

Si una plantilla no se puede cargar en el entorno de desarrollo, hay varias maneras de localizar la causa del problema.

## <a name="validate-the-vstemplate-file"></a>Validación del archivo .vstemplate

Si el archivo *.vstemplate* en una plantilla no cumple el esquema de plantilla de Visual Studio, la plantilla podría no aparecer en el cuadro de diálogo **Nuevo proyecto**.

### <a name="to-validate-the-vstemplate-file"></a>Para validar el archivo .vstemplate

1. Busque el archivo *.zip* que contiene la plantilla.

1. Extraiga el archivo *.zip*.

1. En el menú **Archivo** de Visual Studio, seleccione **Abrir** > **Archivo**.

1. Seleccione el archivo *.vstemplate* para la plantilla y seleccione **Abrir**.

1. Compruebe que el XML del archivo *.vstemplate* cumple el esquema de plantilla. Para obtener más información sobre el esquema *.vstemplate*, vea [Template Schema Reference](../extensibility/visual-studio-template-schema-reference.md) (Referencia de esquema de plantillas).

    > [!NOTE]
    > Para obtener compatibilidad con IntelliSense mientras se crea el archivo *.vstemplate*, agregue un atributo `xmlns` al elemento `VSTemplate` y asígnele un valor de http://schemas.microsoft.com/developer/vstemplate/2005.

1. Guarde y cierre el archivo *.vstemplate*.

1. Seleccione los archivos incluidos en la plantilla, haga clic con el botón derecho y seleccione **Enviar a** > **Carpeta comprimida (en zip)**. Los archivos seleccionados se comprimen en un archivo *.zip*.

1. Coloque el nuevo archivo *.zip* en el mismo directorio que el antiguo.

1. Elimine los archivos de plantilla extraídos y el archivo *.zip* de plantilla antiguo.

## <a name="enable-diagnostic-logging"></a>Habilitación del registro de diagnóstico

Para habilitar el registro de diagnóstico para la detección de plantillas, siga los pasos descritos en [Solución de problemas de detección de plantillas (Extensibilidad)](../extensibility/troubleshooting-template-discovery.md).

## <a name="see-also"></a>Vea también

[Solución de problemas de detección de plantillas (Extensibilidad)](../extensibility/troubleshooting-template-discovery.md)  
[Personalizar plantillas](../ide/customizing-project-and-item-templates.md)  
[Creación de plantillas de proyecto y elemento](../ide/creating-project-and-item-templates.md)  
[Referencia de esquema de plantillas](../extensibility/visual-studio-template-schema-reference.md)