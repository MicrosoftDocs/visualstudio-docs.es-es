---
title: Solución de problemas de carga de plantillas de proyecto y de elemento
ms.date: 01/02/2018
ms.topic: troubleshooting
helpviewer_keywords:
- templates [Visual Studio], troubleshooting
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: 1bef6a460f1a59823930597565b955b591ab48a0
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/01/2020
ms.locfileid: "75591390"
---
# <a name="how-to-troubleshoot-templates"></a>Procedimiento Solucionar problemas de plantillas

Si una plantilla no se puede cargar en el entorno de desarrollo, hay varias maneras de localizar la causa del problema.

## <a name="validate-the-vstemplate-file"></a>Validación del archivo vstemplate

::: moniker range="vs-2017"

Si el archivo *vstemplate* en una plantilla no cumple el esquema de plantilla de Visual Studio, la plantilla podría no aparecer en el cuadro de diálogo **Nuevo proyecto**.

::: moniker-end

::: moniker range=">=vs-2019"

Si el archivo *vstemplate* de una plantilla no cumple el esquema de plantilla de Visual Studio, es posible que la plantilla no aparezca en el cuadro de diálogo en que se creen los proyectos.

::: moniker-end

### <a name="to-validate-the-vstemplate-file"></a>Para validar el archivo vstemplate

1. Busque el archivo *.zip* que contiene la plantilla.

1. Extraiga el archivo *.zip*.

1. En el menú **Archivo** de Visual Studio, seleccione **Abrir** > **Archivo**.

1. Seleccione el archivo *vstemplate* para la plantilla y seleccione **Abrir**.

1. Compruebe que el XML del archivo *vstemplate* cumple el esquema de plantilla. Para más información sobre el esquema *vstemplate*, vea [Template Schema Reference](../extensibility/visual-studio-template-schema-reference.md) (Referencia de esquema de plantillas).

    > [!NOTE]
    > Para obtener compatibilidad con IntelliSense mientras se crea el archivo *vstemplate*, agregue un atributo `xmlns` al elemento `VSTemplate` y asígnele un valor de `http://schemas.microsoft.com/developer/vstemplate/2005`.

1. Guarde y cierre el archivo *vstemplate*.

1. Seleccione los archivos incluidos en la plantilla, haga clic con el botón derecho y seleccione **Enviar a** > **Carpeta comprimida (en zip)** . Los archivos seleccionados se comprimen en un archivo *.zip*.

1. Coloque el nuevo archivo *.zip* en el mismo directorio que el antiguo.

1. Elimine los archivos de plantilla extraídos y el archivo *.zip* de plantilla antiguo.

## <a name="enable-diagnostic-logging"></a>Habilitación del registro de diagnóstico

Para habilitar el registro de diagnóstico para la detección de plantillas, siga los pasos descritos en [Solución de problemas de detección de plantillas (Extensibilidad)](../extensibility/troubleshooting-template-discovery.md).

## <a name="see-also"></a>Vea también

- [Solución de problemas de detección de plantillas (Extensibilidad)](../extensibility/troubleshooting-template-discovery.md)
- [Personalizar plantillas](../ide/customizing-project-and-item-templates.md)
- [Creación de plantillas de proyecto y elemento](../ide/creating-project-and-item-templates.md)
- [Referencia de esquema de plantillas](../extensibility/visual-studio-template-schema-reference.md)
