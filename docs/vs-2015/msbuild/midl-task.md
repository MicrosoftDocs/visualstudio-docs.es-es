---
title: MIDL (tarea) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- VC.Project.VCMidlTool.ServerStubFile
- VC.Project.VCMidlTool.ApplicationConfigurationMode
- VC.Project.VCMidlTool.GenerateServerFiles
- VC.Project.VCMidlTool.ClientStubFile
- VC.Project.VCMidlTool.LocaleID
- VC.Project.VCMidlTool.GenerateClientFiles
- VC.Project.VCMidlTool.SuppressCompilerWarnings
- VC.Project.VCMidlTool.TypeLibFormat
- vc.task.midl
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild (Visual C++), MIDL task
- MIDL task (MSBuild (Visual C++))
ms.assetid: 727efa8c-3336-40b8-8bef-ae6cbd77a422
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9d0398217bb48786067f8392c5e372b0888d060f
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 02/19/2019
ms.locfileid: "54782480"
---
# <a name="midl-task"></a>MIDL (tarea)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Encapsula la herramienta compilador de lenguaje de definición de interfaz de Microsoft (MIDL), midl.exe. Para obtener más información, consulte "Referencia de la línea de comandos de MIDL" en el sitio web de [MSDN](http://go.microsoft.com/fwlink/?LinkId=737).  
  
## <a name="parameters"></a>Parámetros  
 En la siguiente tabla se describen los parámetros de la tarea **MIDL**. La mayoría de los parámetros de tarea, así como algunos conjuntos de parámetros, corresponden a una opción de línea de comandos.  
  
-   **AdditionalIncludeDirectories**  
  
     Parámetro **String[]** opcional.  
  
     Agrega un directorio a la lista de directorios en que se buscan archivos IDL importados, incluidos archivos de encabezado, y archivos de configuración de la aplicación (ACF).  
  
     Para obtener más información, consulte la opción **/I** en "Referencia de la línea de comandos de MIDL" en el sitio web de [MSDN](http://go.microsoft.com/fwlink/?LinkId=737).  
  
-   **AdditionalOptions**  
  
     Parámetro **String** opcional.  
  
     Una lista de opciones de la línea de comandos. Por ejemplo, **"**_/option1 /option2 /option#_". Utilice este parámetro para especificar opciones de la línea de comandos que no están representadas por ningún otro parámetro de la tarea MIDL.  
  
     Para obtener más información, consulte "Referencia de la línea de comandos de MIDL" en el sitio web de [MSDN](http://go.microsoft.com/fwlink/?LinkId=737).  
  
-   **ApplicationConfigurationMode**  
  
     Parámetro **Boolean** opcional.  
  
     Si `true`, le permite utilizar algunas palabras clave ACF en el archivo IDL.  
  
     Para obtener más información, consulte la opción **//app_config** en "Referencia de la línea de comandos de MIDL" en el sitio web de [MSDN](http://go.microsoft.com/fwlink/?LinkId=737).  
  
-   **ClientStubFile**  
  
     Parámetro **String** opcional.  
  
     Especifica el nombre del archivo de código auxiliar de cliente para una interfaz RPC.  
  
     Para obtener más información, consulte la opción **/cstub** en "Referencia de la línea de comandos de MIDL" en el sitio web de [MSDN](http://go.microsoft.com/fwlink/?LinkId=737). Consulte también el parámetro **ServerStubFile** en esta tabla.  
  
-   **CPreprocessOptions**  
  
     Parámetro **String** opcional.  
  
     Especifica las opciones que se deben pasar al preprocesador de C/C#. Especifique una lista delimitada por espacios de opciones de preprocesador.  
  
     Para obtener más información, consulte la opción **/cpp_opt** en "Referencia de la línea de comandos de MIDL" en el sitio web de [MSDN](http://go.microsoft.com/fwlink/?LinkId=737).  
  
-   **DefaultCharType**  
  
     Parámetro **String** opcional.  
  
     Especifica el tipo de carácter predeterminado que el compilador de C utilizará para compilar el código generado.  
  
     Especifique uno de los valores siguientes, cada uno de los cuales corresponde a una opción de línea de comandos.  
  
    |Valor|Opción de la línea de comandos|  
    |-----------|--------------------------|  
    |**Signed**|**/char signed**|  
    |**Unsigned**|**/char unsigned**|  
    |**Ascii**|**/char ascii7**|  
  
     Para obtener más información, consulte la opción **/char** en "Referencia de la línea de comandos de MIDL" en el sitio web de [MSDN](http://go.microsoft.com/fwlink/?LinkId=737).  
  
-   **DllDataFileName**  
  
     Parámetro **String** opcional.  
  
     Especifica el nombre de archivo para el archivo *dlldata* generado para una DLL de proxy.  
  
     Para obtener más información, consulte la opción **/dlldata** en "Referencia de la línea de comandos de MIDL" en el sitio web de [MSDN](http://go.microsoft.com/fwlink/?LinkId=737).  
  
-   **EnableErrorChecks**  
  
     Parámetro **String** opcional.  
  
     Especifica el tipo de error al comprobar que los códigos auxiliares generados funcionarán en tiempo de ejecución.  
  
     Especifique uno de los valores siguientes, cada uno de los cuales corresponde a una opción de línea de comandos.  
  
    |Valor|Opción de la línea de comandos|  
    |-----------|--------------------------|  
    |**Ninguno**|**/error none**|  
    |**EnableCustom**|**/error**|  
    |**All**|**/error all**|  
  
     Para obtener más información, consulte la opción **/error** en "Referencia de la línea de comandos de MIDL" en el sitio web de [MSDN](http://go.microsoft.com/fwlink/?LinkId=737).  
  
-   **ErrorCheckAllocations**  
  
     Parámetro **Boolean** opcional.  
  
     Si `true`, compruebe si hay errores de memoria insuficiente.  
  
     Para obtener más información, consulte la opción **/error allocation** en "Referencia de la línea de comandos de MIDL" en el sitio web de [MSDN](http://go.microsoft.com/fwlink/?LinkId=737).  
  
-   **ErrorCheckBounds**  
  
     Parámetro **Boolean** opcional.  
  
     Si `true`, comprueba el tamaño de la variable conforme y diferentes matrices con la especificación de longitud de transmisión.  
  
     Para obtener más información, consulte la opción **/error bounds_check** en "Referencia de la línea de comandos de MIDL" en el sitio web de [MSDN](http://go.microsoft.com/fwlink/?LinkId=737).  
  
-   **ErrorCheckEnumRange**  
  
     Parámetro **Boolean** opcional.  
  
     Si `true`, comprueba que los valores de enumeración están en un intervalo permitido.  
  
     Para obtener más información, consulte la opción **/error enum** en la Ayuda de la línea de comandos (**/?**) de midl.exe.  
  
-   **ErrorCheckRefPointers**  
  
     Parámetro **Boolean** opcional.  
  
     Si `true`, compruebe que ningún puntero de referencia nula se pasa a los códigos auxiliares del cliente.  
  
     Para obtener más información, consulte la opción **/error ref** en "Referencia de la línea de comandos de MIDL" en el sitio web de [MSDN](http://go.microsoft.com/fwlink/?LinkId=737).  
  
-   **ErrorCheckStubData**  
  
     Parámetro **Boolean** opcional.  
  
     Si `true`, genera un código auxiliar que detecta las excepciones de anulación del cálculo de referencias en el servidor y las propaga al cliente.  
  
     Para obtener más información, consulte la opción **/error stub_data** en "Referencia de la línea de comandos de MIDL" en el sitio web de [MSDN](http://go.microsoft.com/fwlink/?LinkId=737).  
  
-   **GenerateClientFiles**  
  
     Parámetro **String** opcional.  
  
     Especifica si el compilador genera archivos de origen de C del cliente para una interfaz RPC.  
  
     Especifique uno de los valores siguientes, cada uno de los cuales corresponde a una opción de línea de comandos.  
  
    |Valor|Opción de la línea de comandos|  
    |-----------|--------------------------|  
    |**Ninguno**|**/client none**|  
    |**Stub**|**/client stub**|  
  
     Para obtener más información, consulte la opción **/client** en "Referencia de la línea de comandos de MIDL" en el sitio web de [MSDN](http://go.microsoft.com/fwlink/?LinkId=737).  
  
-   **GenerateServerFiles**  
  
     Parámetro **String** opcional.  
  
     Especifica si el compilador genera archivos de origen de C del servidor para una interfaz RPC.  
  
     Especifique uno de los valores siguientes, cada uno de los cuales corresponde a una opción de línea de comandos.  
  
    |Valor|Opción de la línea de comandos|  
    |-----------|--------------------------|  
    |**Ninguno**|**/server none**|  
    |**Stub**|**/server stub**|  
  
     Para obtener más información, consulte la opción **/server** en "Referencia de la línea de comandos de MIDL" en el sitio web de [MSDN](http://go.microsoft.com/fwlink/?LinkId=737).  
  
-   **GenerateStublessProxies**  
  
     Parámetro **Boolean** opcional.  
  
     Si `true`, genera códigos auxiliares totalmente interpretados junto con servidores proxy sin código auxiliar para las interfaces de objetos.  
  
     Para obtener más información, consulte la opción **/Oicf** en "Referencia de la línea de comandos de MIDL" en el sitio web de [MSDN](http://go.microsoft.com/fwlink/?LinkId=737).  
  
-   **GenerateTypeLibrary**  
  
     Parámetro **Boolean** opcional.  
  
     Si `true`, no se genera ningún archivo de biblioteca de tipo (.tlb).  
  
     Para obtener más información, consulte la opción **/notlb** en "Referencia de la línea de comandos de MIDL" en el sitio web de [MSDN](http://go.microsoft.com/fwlink/?LinkId=737).  
  
-   **HeaderFileName**  
  
     Parámetro **String** opcional.  
  
     Especifica el nombre del archivo de encabezado generado.  
  
     Para obtener más información, consulte la opción **/h** o **/header** en "Referencia de la línea de comandos de MIDL" en el sitio web de [MSDN](http://go.microsoft.com/fwlink/?LinkId=737).  
  
-   **IgnoreStandardIncludePath**  
  
     Parámetro **Boolean** opcional.  
  
     Si `true`, la tarea MIDL solo busca en los directorios especificados mediante el modificador **AdditionalIncludeDirectories** y omite tanto el directorio actual como los directorios especificados por la variable de entorno INCLUDE.  
  
     Para obtener más información, consulte la opción **/no_def_idir** en "Referencia de la línea de comandos de MIDL" en el sitio web de [MSDN](http://go.microsoft.com/fwlink/?LinkId=737).  
  
-   **InterfaceIdentifierFileName**  
  
     Parámetro **String** opcional.  
  
     Especifica el nombre del *archivo del identificador de interfaz* para una interfaz COM. Esto invalida el nombre predeterminado obtenido al agregar "_i.c" al nombre de archivo IDL.  
  
     Para obtener más información, consulte la opción **/iid** en "Referencia de la línea de comandos de MIDL" en el sitio web de [MSDN](http://go.microsoft.com/fwlink/?LinkId=737).  
  
-   **LocaleID**  
  
     Parámetro **int** opcional.  
  
     Especifica el *identificador de configuración regional* que habilita el uso de caracteres internacionales en archivos de entrada, nombres de archivo y rutas de acceso de directorio. Especificar un identificador de configuración regional decimal.  
  
     Para obtener más información, consulte la opción **/lcid** en "Referencia de la línea de comandos de MIDL" en el sitio web de [MSDN](http://go.microsoft.com/fwlink/?LinkId=737). Consulte también "Identificadores de configuración regional asignados por Microsoft" en MSDN.  
  
-   **MkTypLibCompatible**  
  
     Parámetro **Boolean** opcional.  
  
     Si `true`, requiere que el formato del archivo de entrada sea compatible con mktyplib.exe versión 2.03.  
  
     Para obtener más información, consulte la opción **/mktyplib203** en "Referencia de la línea de comandos de MIDL" en el sitio web de [MSDN](http://go.microsoft.com/fwlink/?LinkId=737). Consulte también "Sintaxis de archivos ODL" en el sitio web de MSDN.  
  
-   **OutputDirectory**  
  
     Parámetro **String** opcional.  
  
     Especifica el directorio predeterminado en que la tarea MIDL escribe los archivos de salida.  
  
     Para obtener más información, consulte la opción **/out** en "Referencia de la línea de comandos de MIDL" en el sitio web de [MSDN](http://go.microsoft.com/fwlink/?LinkId=737).  
  
-   **PreprocessorDefinitions**  
  
     Parámetro **String[]** opcional.  
  
     Especifica uno o más *defines*; es decir, un nombre y un valor opcional que se pasará al preprocesador de C como si lo hiciera una directiva de `#define`. El formato de cada define es *name[=value]*.  
  
     Para obtener más información, consulte la opción **/D** en "Referencia de la línea de comandos de MIDL" en el sitio web de [MSDN](http://go.microsoft.com/fwlink/?LinkId=737). Consulte también el parámetro **UndefinePreprocessorDefinitions** en esta tabla.  
  
-   **ProxyFileName**  
  
     Parámetro **String** opcional.  
  
     Especifica el nombre del archivo de proxy de interfaz para una interfaz COM.  
  
     Para obtener más información, consulte la opción **/proxy** en "Referencia de la línea de comandos de MIDL" en el sitio web de [MSDN](http://go.microsoft.com/fwlink/?LinkId=737).  
  
-   **RedirectOutputAndErrors**  
  
     Parámetro **String** opcional.  
  
     Redirige la salida, como los mensajes de error y advertencias, desde la salida estándar al archivo especificado.  
  
     Para obtener más información, consulte la opción **/o** en "Referencia de la línea de comandos de MIDL" en el sitio web de [MSDN](http://go.microsoft.com/fwlink/?LinkId=737).  
  
-   **ServerStubFile**  
  
     Parámetro **String** opcional.  
  
     Especifica el nombre del archivo de código auxiliar de servidor para una interfaz RPC.  
  
     Para obtener más información, consulte la opción **/sstub** en "Referencia de la línea de comandos de MIDL" en el sitio web de [MSDN](http://go.microsoft.com/fwlink/?LinkId=737). Consulte también el parámetro **ClientStubFile** en esta tabla.  
  
-   **Source**  
  
     Parámetro `ITaskItem[]` requerido.  
  
     Especifica una lista de archivos de código fuente, separados por espacios.  
  
-   **StructMemberAlignment**  
  
     Parámetro **String** opcional.  
  
     Especifica la alineación (*el nivel de empaquetado*) de estructuras en el sistema de destino.  
  
     Especifique uno de los valores siguientes, cada uno de los cuales corresponde a una opción de línea de comandos.  
  
    |Valor|Opción de la línea de comandos|  
    |-----------|--------------------------|  
    |**NotSet**|*\<none>*|  
    |**1**|**/Zp1**|  
    |**2**|**/Zp2**|  
    |**4**|**/Zp4**|  
    |**8**|**/Zp8**|  
  
     Para obtener más información, consulte la opción **/Zp** en "Referencia de la línea de comandos de MIDL" en el sitio web de [MSDN](http://go.microsoft.com/fwlink/?LinkId=737). La opción **/Zp** es equivalente a la opción **/pack** y a la antigua opción **/align**.  
  
-   **SuppressCompilerWarnings**  
  
     Parámetro **Boolean** opcional.  
  
     Si `true`, suprime los mensajes de advertencia de la tarea MIDL.  
  
     Para obtener más información, consulte la opción **/no_warn** en "Referencia de la línea de comandos de MIDL" en el sitio web de [MSDN](http://go.microsoft.com/fwlink/?LinkId=737).  
  
-   **SuppressStartupBanner**  
  
     Parámetro `Boolean` opcional.  
  
     Si es `true`, evita que se muestre el copyright y el mensaje de número de versión cuando la tarea se inicia.   
  
     Para obtener más información, consulte la opción **/nologo** en "Referencia de la línea de comandos de MIDL" en el sitio web de [MSDN](http://go.microsoft.com/fwlink/?LinkId=737).  
  
-   **TargetEnvironment**  
  
     Parámetro **String** opcional.  
  
     Especifica el entorno en el que se ejecuta la aplicación.  
  
     Especifique uno de los valores siguientes, cada uno de los cuales corresponde a una opción de línea de comandos.  
  
    |Valor|Opción de la línea de comandos|  
    |-----------|--------------------------|  
    |**NotSet**|*\<none>*|  
    |**Win32**|**/env win32**|  
    |**Itanium**|**/env ia64**|  
    |**X64**|**/env x64**|  
  
     Para obtener más información, consulte la opción **/env** en "Referencia de la línea de comandos de MIDL" en el sitio web de [MSDN](http://go.microsoft.com/fwlink/?LinkId=737).  
  
-   **TrackerLogDirectory**  
  
     Parámetro `String` opcional.  
  
     Especifica el directorio intermedio en que se almacenan los registros de seguimiento para esta tarea.  
  
-   **TypeLibFormat**  
  
     Parámetro **String** opcional.  
  
     Especifica el formato de archivo de biblioteca de tipos.  
  
     Especifique uno de los valores siguientes, cada uno de los cuales corresponde a una opción de línea de comandos.  
  
    |Valor|Opción de la línea de comandos|  
    |-----------|--------------------------|  
    |**NewFormat**|**/newtlb**|  
    |**OldFormat**|**/oldtlb**|  
  
     Para obtener más información, consulte las opciones **/newtlb** y **/oldtlb** en "Referencia de la línea de comandos de MIDL" en el sitio web de [MSDN](http://go.microsoft.com/fwlink/?LinkId=737).  
  
-   **TypeLibraryName**  
  
     Parámetro **String** opcional.  
  
     Especifica el nombre del archivo de biblioteca de tipos.  
  
     Para obtener más información, consulte la opción **/tlb** en "Referencia de la línea de comandos de MIDL" en el sitio web de [MSDN](http://go.microsoft.com/fwlink/?LinkId=737).  
  
-   **UndefinePreprocessorDefinitions**  
  
     Parámetro **String[]** opcional.  
  
     Quita cualquier definición anterior de un nombre, pasando el nombre al preprocesador de C como si lo hiciera una directiva de `#undefine`. Especifique uno o más nombres definidos previamente.  
  
     Para obtener más información, consulte la opción **/U** en "Referencia de la línea de comandos de MIDL" en el sitio web de [MSDN](http://go.microsoft.com/fwlink/?LinkId=737). Consulte también el parámetro **PreprocessorDefinitions** en esta tabla.  
  
-   **ValidateAllParameters**  
  
     Parámetro `Boolean` opcional.  
  
     Si `true`, genera información de comprobación de errores adicional que se utiliza para realizar comprobaciones de integridad en tiempo de ejecución. Si `false`, no se genera la información de comprobación de errores.  
  
     Para obtener más información, consulte las opciones **/robust** y **/no_robust** en "Referencia de la línea de comandos de MIDL" en el sitio web de [MSDN](http://go.microsoft.com/fwlink/?LinkId=737).  
  
-   **WarnAsError**  
  
     Parámetro `Boolean` opcional.  
  
     Si `true`, trata todas las advertencias como errores.  
  
     Si no se especifica el parámetro de la tarea MIDL **WarningLevel**, las advertencias del nivel 1, el nivel predeterminado, se tratan como errores.  
  
     Para obtener más información, consulte la opción **/WX** en "Referencia de la línea de comandos de MIDL" en el sitio web de [MSDN](http://go.microsoft.com/fwlink/?LinkId=737). Consulte también el parámetro **WarningLevel** en esta tabla.  
  
-   **WarningLevel**  
  
     Parámetro **String** opcional.  
  
     Especifica la gravedad (*nivel de advertencia*) de las advertencias que se emiten. Para un valor de 0 no se emite ninguna advertencia. En cambio, se emite una advertencia si su nivel de advertencia es numéricamente menor o igual que el valor especificado.  
  
     Especifique uno de los valores siguientes, cada uno de los cuales corresponde a una opción de línea de comandos.  
  
    |Valor|Opción de la línea de comandos|  
    |-----------|--------------------------|  
    |**0**|**/W0**|  
    |**1**|**/W1**|  
    |**2**|**/W2**|  
    |**3**|**/W3**|  
    |**4**|**/W4**|  
  
     Para obtener más información, consulte la opción **/W** en "Referencia de la línea de comandos de MIDL" en el sitio web de [MSDN](http://go.microsoft.com/fwlink/?LinkId=737). Consulte también el parámetro **WarnAsError** en esta tabla.  
  
## <a name="remarks"></a>Comentarios  
  
## <a name="see-also"></a>Vea también  
 [Referencia de tareas](../msbuild/msbuild-task-reference.md)
