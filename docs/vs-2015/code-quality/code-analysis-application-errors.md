---
title: Errores de aplicación de análisis de código | Documentos de Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- errors [Visual Studio ALM], code analysis
- code analysis, errors
- managed code, code analysis errors
- code analysis, policy errors
ms.assetid: d8fd9475-ac9b-4085-b5a3-b0c807922cac
caps.latest.revision: 25
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 66d611903c71cc526c01c1062c85ceef2e7975f5
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49225022"
---
# <a name="code-analysis-application-errors"></a>Errores de la aplicación de análisis de código
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
En esta sección es una referencia de los mensajes de error generados por la herramienta de análisis de código administrado. Para obtener ayuda sobre un mensaje de error específico, escriba el número de error en la **buscar** cuadro en el índice.

## <a name="in-this-section"></a>En esta sección

|||
|-|-|
|[CA0001](ca0001.md)|Se generó una excepción dentro de la herramienta de análisis de código administrado que no indica una condición de error esperado.|
|[CA0051](ca0051.md)|No se seleccionaron reglas.|
|[CA0052](ca0052.md)|No se seleccionaron destinos para analizar.|
|[CA0053](ca0053.md)|No se pudo cargar el ensamblado de regla.|
|[CA0054](ca0054.md)|Un ensamblado de regla personalizada tiene recursos XML no válidos.|
|[CA0055](ca0055.md)|No se pudo cargar el archivo:\<ruta de acceso >|
|[CA0056](ca0056.md)|Un archivo de proyecto tiene una versión incorrecta de la herramienta de análisis.|
|[CA0057](ca0057.md)|No se puede asignar las infracciones en el conjunto actual de destinos y reglas.|
|[CA0058](ca0058.md)|No se puede cargar los ensamblados referenciados.|
|[CA0059](ca0059.md)|Error del conmutador de línea de comandos.|
|[CA0060](ca0060.md)|No se puede cargar ensamblados al que hace referencia indirectamente.|
|[CA0061](ca0061.md)|La regla '*RuleId*' no se encontró.|
|[CA0062](ca0062.md)|La regla '*RuleId*'hace referencia en el conjunto de reglas'*RuleSetName*' no se encontró.|
|[CA0063](ca0063.md)|No se pudo cargar el archivo de conjunto de reglas o uno de sus archivos de conjunto de reglas dependientes.|
|[CA0064](ca0064.md)|Ningún análisis se realizan porque el conjunto de reglas especificada no contiene ninguna regla de FxCop.|
|[CA0065](ca0065.md)|Construcción de metadatos no admitido: tipo '*TypeName*'contiene una propiedad y un campo con el mismo nombre'*PropertyFieldName*'|
|[CA0066](ca0066.md)|El valor '*VersionID*' proporcionado para el **/targetframeworkversion** no es una versión reconocida.|
|[CA0067](ca0067.md)|No se encontró el directorio.|
|[CA0068](ca0068.md)|Depuración no se encuentra la información de ensamblado de destino *'AssemblyName'*.|
|[CA0069](ca0069.md)|Con la plataforma alternativa. *FrameworkVersion1* no se pudo encontrar. Uso de *FrameworkVersion2* en su lugar. Para obtener los mejores resultados análisis Asegúrese de que la versión correcta de .NET Framework está instalada.|
|[CA0070](ca0070.md)|No se puede cargar el ensamblado o tipo debido a permisos de seguridad.|
|[CA0501](ca0501.md)|No se puede leer el informe de salida.|
|[CA0502](ca0502.md)|Idioma no admitido.|
|[CA0503](ca0503.md))|La propiedad está obsoleta. Utilice la propiedad sustituye|
|[CA0504](ca0504.md)|Directorio de la regla se omitió porque no existe|
|[CA0505](ca0505.md)|La propiedad está obsoleta. Utilice la propiedad sustituye|
|[Errores de FxCopCmd](fxcopcmd-errors.md)|Errores de análisis de código administrado.|
|[Code Analysis Policy Errors](../code-quality/code-analysis-policy-errors.md)|Errores de directiva de protección de análisis de código.|

## <a name="related-sections"></a>Secciones relacionadas

- [Instrucciones para escribir código seguro](http://msdn.microsoft.com/en-us/9892fd19-45cd-44b6-9fa8-10f1b5cb6ea4)
- [Analizar la calidad del código administrado](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md)
- [Recursos para solucionar problemas de errores en las herramientas de administración del ciclo de vida de aplicación](http://msdn.microsoft.com/library/76ca8f76-1e2d-4b55-89e2-bd59e4abe74c)