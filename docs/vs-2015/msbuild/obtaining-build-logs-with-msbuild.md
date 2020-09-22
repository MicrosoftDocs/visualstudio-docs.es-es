---
title: Obtener registros de compilación con MSBuild | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, logging
- logging [MSBuild]
ms.assetid: 6ba9a754-9cc0-4fed-9fc8-4dcd3926a031
caps.latest.revision: 30
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c88288a7bed453ca14e9c14fd43706b97be04044
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "90842514"
---
# <a name="obtaining-build-logs-with-msbuild"></a>Obtener registros de compilación con MSBuild
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Mediante el uso de modificadores con MSBuild, puede especificar la cantidad de datos de compilación que quiere revisar y si quiere guardarlos en uno o más archivos. También puede especificar un registrador personalizado para recopilar datos de compilación. Para obtener información acerca de los modificadores de la línea de comandos de MSBuild que no se tratan en este tema, vea [referencia de la línea de comandos](../msbuild/msbuild-command-line-reference.md).  
  
> [!NOTE]
> Si compila proyectos mediante el IDE de Visual Studio, puede solucionar las compilaciones mediante la revisión de los registros de compilación. Para obtener más información, vea [Cómo: Ver, guardar y configurar archivos de registro de compilación](../ide/how-to-view-save-and-configure-build-log-files.md).  
  
## <a name="setting-the-level-of-detail"></a>Establecer el nivel de detalle  
 Cuando compila un proyecto mediante el uso de MSBuild sin especificar un nivel de detalle, la siguiente información aparece en el registro de salida:  
  
- Errores, advertencias y mensajes que están clasificados como muy importantes.  
  
- Algunos eventos de estado.  
  
- Un resumen de la compilación.  
  
  Con el modificador **/verbosity** (**/v**), puede controlar la cantidad de datos que aparecen en el registro de salida. Para solucionar el problema, utilice un nivel de detalle del `detailed` (`d`) o `diagnostic` (`diag`), que proporciona más información.  
  
  El proceso de compilación puede ser más lento cuando se establece el **/verbosity** en `detailed` e incluso más lentamente al establecer el valor de **/verbosity** en `diagnostic` .  
  
```  
msbuild MyProject.proj /t:go /v:diag  
```  
  
## <a name="saving-the-build-log-to-a-file"></a>Guardar el registro de compilación en un archivo  
 Puede usar el modificador **/fileLogger** (**FL**) para guardar los datos de compilación en un archivo. En el ejemplo siguiente, los datos de compilación se guardan en un archivo denominado `msbuild.log`.  
  
```  
msbuild MyProject.proj /t:go /fileLogger  
```  
  
 En el ejemplo siguiente, el archivo de registro se denomina `MyProjectOutput.log`, y el nivel de detalle de la salida del registro se establece en `diagnostic`. Estos dos valores se especifican mediante el **/filelogparameters** `flp` modificador/filelogparameters ().  
  
```  
msbuild MyProject.proj /t:go /fl /flp:logfile=MyProjectOutput.log;verbosity=diagnostic  
```  
  
 Para obtener más información, vea [referencia de la línea de comandos](../msbuild/msbuild-command-line-reference.md).  
  
## <a name="saving-the-log-output-to-multiple-files"></a>Guardar la salida del registro en varios archivos  
 En el ejemplo siguiente se guarda el registro completo en `msbuild1.log`, solo los errores en `JustErrors.log` y solo las advertencias en `JustWarnings.log`. En el ejemplo se utilizan números de archivo para cada uno de los tres archivos. Los números de archivo se especifican justo después de los modificadores **/FL** y **/FLP** (por ejemplo, `/fl1` y `/flp1` ).  
  
 Los **/filelogparameters** `flp` Modificadores/filelogparameters () para los archivos 2 y 3 especifican qué asignar nombre a cada archivo y qué incluir en cada archivo. No se especifica ningún nombre para el archivo 1, por lo que se utiliza el nombre predeterminado de `msbuild1.log`.  
  
```  
msbuild MyProject.proj /t:go /fl1 /fl2 /fl3 /flp2:logfile=JustErrors.log;errorsonly /flp3:logfile=JustWarnings.log;warningsonly  
  
```  
  
 Para obtener más información, vea [referencia de la línea de comandos](../msbuild/msbuild-command-line-reference.md).  
  
## <a name="using-a-custom-logger"></a>Usar un registrador personalizado  
 Para escribir su propio registrador, cree un tipo administrado que implemente la interfaz <xref:Microsoft.Build.Framework.ILogger>. Puede usar un registrador personalizado, por ejemplo, para enviar errores de compilación por correo electrónico o para registrarlos en una base de datos o en un archivo XML. Para obtener más información, vea [loggers de compilación](../msbuild/build-loggers.md).  
  
 En la línea de comandos de MSBuild, especifique el registrador personalizado mediante el modificador **/Logger** . También puede usar el modificador **/noconsolelogger** para deshabilitar el registrador de consola predeterminado.  
  
## <a name="see-also"></a>Consulte también  
 <xref:Microsoft.Build.Framework.LoggerVerbosity>   
 [Registradores de compilación](../msbuild/build-loggers.md)   
 [Registro en un entorno de varios procesadores](../msbuild/logging-in-a-multi-processor-environment.md)   
 [Crear registradores de reenvío](../msbuild/creating-forwarding-loggers.md)   
 [Conceptos de MSBuild](../msbuild/msbuild-concepts.md)
