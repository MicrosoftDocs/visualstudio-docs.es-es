---
title: Obtener registros de compilación con MSBuild | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, logging
- logging [MSBuild]
ms.assetid: 6ba9a754-9cc0-4fed-9fc8-4dcd3926a031
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d372bf84d6b43547be160a50e52afffccd42bc89
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "55035580"
---
# <a name="obtain-build-logs-with-msbuild"></a>Obtener registros de compilación con MSBuild

Mediante el uso de modificadores con MSBuild, puede especificar la cantidad de datos de compilación que quiere revisar y si quiere guardarlos en uno o más archivos. También puede especificar un registrador personalizado para recopilar datos de compilación. Para información sobre los modificadores de la línea de comandos de MSBuild que no se tratan en este tema, consulte [Referencia de la línea de comandos](../msbuild/msbuild-command-line-reference.md).  
  
> [!NOTE]
> Si compila proyectos mediante el IDE de Visual Studio, puede solucionar las compilaciones mediante la revisión de los registros de compilación. Para obtener más información, vea [Cómo: Ver, guardar y configurar archivos de registro de compilación](../ide/how-to-view-save-and-configure-build-log-files.md).
  
## <a name="set-the-level-of-detail"></a>Establecimiento del nivel de detalle  

 Cuando compila un proyecto mediante el uso de MSBuild sin especificar un nivel de detalle, la siguiente información aparece en el registro de salida:  
  
- Errores, advertencias y mensajes que están clasificados como muy importantes.  
  
- Algunos eventos de estado.  
  
- Un resumen de la compilación.  

Mediante el uso del modificador **-verbosity** (**-v**), puede controlar la cantidad de datos que aparecen en el registro de salida. Para solucionar el problema, utilice un nivel de detalle del `detailed` (`d`) o `diagnostic` (`diag`), que proporciona más información.  

El proceso de compilación puede ser más lento cuando **-verbosity** se establece en `detailed` e incluso más lento al establecer **-verbosity** en `diagnostic`.  

```cmd
msbuild MyProject.proj -t:go -v:diag  
```  

### <a name="verbosity-settings"></a>Configuración de nivel de detalle

En la siguiente tabla se muestra cómo el nivel de detalle de registro (valores de columna) afecta a qué tipos de mensaje (valores de fila) se registran.

|                                       | Quiet | Minimal | Normal | Detallado | Diagnóstico |
|---------------------------------------|:-----:|:-------:|:------:|:--------:|:----------:|
| Errores                                |   ✅   |    ✅    |    ✅   |     ✅    |      ✅     |
| Advertencias                              |   ✅   |    ✅    |    ✅   |     ✅    |      ✅     |
| Mensajes de gran importancia              |       |    ✅    |    ✅   |     ✅    |      ✅     |
| Mensajes con una importancia normal           |       |         |    ✅   |     ✅    |      ✅     |
| Mensajes con una importancia baja              |       |         |        |     ✅    |      ✅     |
| Información adicional del motor MSBuild |       |         |        |          |      ✅     |

## <a name="save-the-build-log-to-a-file"></a>Guardar el registro de compilación en un archivo  

Puede usar el modificador **-fileLogger** (**fl**) para guardar los datos de compilación en un archivo. En el ejemplo siguiente, los datos de compilación se guardan en un archivo denominado *msbuild.log*.  

```cmd  
msbuild MyProject.proj -t:go -fileLogger  
```  

 En el ejemplo siguiente, el archivo de registro se denomina *MyProjectOutput.log*, y el nivel de detalle de la salida del registro se establece en `diagnostic`. Puede especificar las dos configuraciones mediante el modificador **-filelogparameters** (`flp`).  

```cmd  
msbuild MyProject.proj -t:go -fl -flp:logfile=MyProjectOutput.log;verbosity=diagnostic  
```  

 Para más información, consulte [Referencia de la línea de comandos](../msbuild/msbuild-command-line-reference.md).  
  
## <a name="save-the-log-output-to-multiple-files"></a>Guardar la salida de registro en varios archivos  

 En el ejemplo siguiente se guarda el registro completo en *msbuild1.log*, solo los errores en *JustErrors.log* y solo las advertencias en *JustWarnings.log*. En el ejemplo se utilizan números de archivo para cada uno de los tres archivos. Los números de archivo se especifican justo después de los modificadores **-fl** y **-flp** (por ejemplo, `-fl1` y `-flp1`).  
  
 Los modificadores **-filelogparameters** (`flp`) para los archivos 2 y 3 especifican el nombre de cada archivo y qué se va a incluir en cada archivo. No se especifica ningún nombre para el archivo 1, por lo que se utiliza el nombre predeterminado de *msbuild1.log*.  

```cmd  
msbuild MyProject.proj -t:go -fl1 -fl2 -fl3 -flp2:logfile=JustErrors.log;errorsonly -flp3:logfile=JustWarnings.log;warningsonly  
```  

 Para más información, consulte [Referencia de la línea de comandos](../msbuild/msbuild-command-line-reference.md).  

## <a name="save-a-binary-log"></a>Guardar un registro binario

Puede guardar el registro en formato comprimido y binario con el modificador **-binaryLogger** (**bl**). Este registro incluye una descripción detallada del proceso de compilación y puede ser leído por determinadas herramientas de análisis de registro.

En el ejemplo siguiente, se crea un archivo de registro binario llamado *binarylogfilename*.

```cmd  
/bl:binarylogfilename.binlog
``` 

Para más información, consulte [Referencia de la línea de comandos](../msbuild/msbuild-command-line-reference.md).  

## <a name="use-a-custom-logger"></a>Uso de un registrador personalizado  

 Para escribir su propio registrador, cree un tipo administrado que implemente la interfaz <xref:Microsoft.Build.Framework.ILogger>. Puede usar un registrador personalizado, por ejemplo, para enviar errores de compilación por correo electrónico o para registrarlos en una base de datos o en un archivo XML. Para más información, consulte [Registradores de compilación](../msbuild/build-loggers.md).  
  
 En la línea de comandos de MSBuild, especifique el registrador personalizado mediante el modificador **-logger**. También puede utilizar el modificador **-noconsolelogger** para desactivar el registrador de consola predeterminado.  
  
## <a name="see-also"></a>Vea también  

 <xref:Microsoft.Build.Framework.LoggerVerbosity>   
 [Registradores de compilación](../msbuild/build-loggers.md)   
 [Registrar en un entorno de varios procesadores](../msbuild/logging-in-a-multi-processor-environment.md)   
 [Crear registradores de reenvío](../msbuild/creating-forwarding-loggers.md)   
 [Conceptos de MSBuild](../msbuild/msbuild-concepts.md)