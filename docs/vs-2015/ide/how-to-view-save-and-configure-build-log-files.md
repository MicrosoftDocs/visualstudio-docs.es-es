---
title: 'Cómo: Ver, guardar y configurar archivos de registro de compilación | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 75d38b76-26d6-4f43-bbe7-cbacd7cc81e7
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ffc1c620136c55c42f3468129ed164075d762bff
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "72670504"
---
# <a name="how-to-view-save-and-configure-build-log-files"></a>Cómo: Ver, guardar y configurar archivos de registro de compilación
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Después de compilar un proyecto en el IDE de Visual Studio, puede ver información sobre la compilación en la ventana **Salida**. Con esta información puede, por ejemplo, solucionar un error de compilación. En el caso de los proyectos de C++, también puede ver la misma información en un archivo .txt que se crea y se guarda automáticamente. Si se trata de proyectos de código administrado, puede copiar y pegar la información de la ventana **Salida** en un archivo .txt y guardarlo donde quiera. También puede usar el IDE para especificar qué tipo de información quiere ver para cada compilación.

 Si compila un proyecto mediante MSBuild, puede crear un archivo .txt para guardar la información de la compilación. Para obtener más información, vea [Obtener registros de compilación](../msbuild/obtaining-build-logs-with-msbuild.md).

### <a name="to-view-the-build-log-file-for-a-c-project"></a>Para ver el archivo de registro de compilación de un proyecto de C++

1. En el explorador de **Windows** o el **Explorador de archivos**, abra el archivo siguiente: \\ . ..\Visual Studio *versión*\projects \\ *projectname* \\ *projectname*\debug \\ *projectname*. txt

### <a name="to-create-a-build-log-file-for-a-managed-code-project"></a>Para crear un archivo de registro de compilación para un proyecto de código administrado

1. En la barra de menús, elija **Compilar**, **Compilar solución**.

2. En la ventana **salida** , resalte la información de la compilación y, a continuación, cópiela en el portapapeles.

3. Abra un editor de texto, como el Bloc de notas, pegue la información en el archivo y guárdelo.

### <a name="to-change-the-amount-of-information-included-in-the-build-log"></a>Para cambiar el volumen de información incluida en el registro de compilación

1. En la barra de menús, elija **herramientas**, **Opciones**.

2. En la página **Proyectos y soluciones**, elija la página **Compilar y ejecutar**.

3. En la lista **Detalles de la salida de la compilación del proyecto de MSBuild**, seleccione uno de los valores siguientes y, después, elija el botón **Aceptar**.

    |Nivel de detalle|Descripción|
    |---------------------|-----------------|
    |Quiet|Muestra un resumen solo de la compilación.|
    |Minimal|Muestra un resumen de la compilación y los errores, las advertencias y los mensajes que están clasificados como muy importantes.|
    |Normal|Muestra un resumen de la compilación; los errores, las advertencias y los mensajes que están clasificados como muy importantes; y los pasos principales de la compilación. Este es el nivel de detalle que se usará con más frecuencia.|
    |Detallado|Muestra un resumen de la compilación; los errores, las advertencias y los mensajes que están clasificados como muy importantes; todos los pasos de la compilación; y los mensajes que están clasificados como de importancia normal.|
    |Diagnóstico|Muestra todos los datos que están disponibles para la compilación. Puede usar este nivel de detalle para ayudar a depurar problemas con los scripts de compilación personalizada y otros problemas de compilación.|

     Para obtener más información, vea [cuadro de diálogo Opciones, proyectos y soluciones, compilar y ejecutar](../ide/reference/options-dialog-box-projects-and-solutions-build-and-run.md) y <xref:Microsoft.Build.Framework.LoggerVerbosity> .

    > [!IMPORTANT]
    > Debe volver a generar el proyecto para que los cambios surtan efecto en la ventana de **salida** (todos los proyectos) y el archivo *projectname*. txt (solo proyectos de C++).

## <a name="see-also"></a>Consulte también
 [Obtener registros de compilación](../msbuild/obtaining-build-logs-with-msbuild.md) [crear y limpiar proyectos y soluciones en Visual Studio](../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md) [compilando y compilando](../ide/compiling-and-building-in-visual-studio.md)
