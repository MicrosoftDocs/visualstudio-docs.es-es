---
title: MIDL (tarea) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1affc4d84b8ea44cbaed51f656c8a3e97e04f97a
ms.sourcegitcommit: d462dd10746624ad139f1db04edd501e7737d51e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/29/2018
ms.locfileid: "50219814"
---
# <a name="midl-task"></a>MIDL (tarea)
Incluye la herramienta de compilación Lenguaje de definición de interfaz de Microsoft (MIDL), *midl.exe*. Para obtener más información, vea [MIDL command-line reference](https://docs.microsoft.com/windows/desktop/Midl/midl-command-line-reference) (Referencia de la línea de comandos de MIDL).  
  
## <a name="parameters"></a>Parámetros  
 A continuación se describen los parámetros de la tarea **MIDL**. La mayoría de los parámetros de tarea, así como algunos conjuntos de parámetros, corresponden a una opción de línea de comandos.  
  
-   **AdditionalIncludeDirectories**  
  
     Parámetro **String[]** opcional.  
  
     Agrega un directorio a la lista de directorios en que se buscan archivos IDL importados, incluidos archivos de encabezado, y archivos de configuración de la aplicación (ACF).  
  
     Para obtener más información, vea la opción **/I** en [MIDL command-line reference](https://docs.microsoft.com/windows/desktop/Midl/midl-command-line-reference) (Referencia de la línea de comandos de MIDL).  
  
-   **AdditionalOptions**  
  
     Parámetro **String** opcional.  
  
     Una lista de opciones de la línea de comandos. Por ejemplo, /\<option1> /\<option2> /\<option#>. Utilice este parámetro para especificar opciones de la línea de comandos que no están representadas por ningún otro parámetro de la tarea MIDL.  
  
     Para obtener más información, vea [MIDL command-line reference](https://docs.microsoft.com/windows/desktop/Midl/midl-command-line-reference) (Referencia de la línea de comandos de MIDL).  
  
-   **ApplicationConfigurationMode**  
  
     Parámetro **Boolean** opcional.  
  
     Si `true`, le permite utilizar algunas palabras clave ACF en el archivo IDL.  
  
     Para obtener más información, vea la opción **/app_config** en [MIDL command-line reference](https://docs.microsoft.com/windows/desktop/Midl/midl-command-line-reference) (Referencia de la línea de comandos de MIDL).  
  
-   **ClientStubFile**  
  
     Parámetro **String** opcional.  
  
     Especifica el nombre del archivo de código auxiliar de cliente para una interfaz RPC.  
  
     Para obtener más información, vea la opción **/cstub** en [MIDL command-line reference](https://docs.microsoft.com/windows/desktop/Midl/midl-command-line-reference) (Referencia de la línea de comandos de MIDL). Consulte también el parámetro **ServerStubFile** en esta tabla.  
  
-   **CPreprocessOptions**  
  
     Parámetro **String** opcional.  
  
     Especifica las opciones que se deben pasar al preprocesador de C/C#. Especifique una lista delimitada por espacios de opciones de preprocesador.  
  
     Para obtener más información, vea la opción **/cpp_opt** en [MIDL command-line reference](https://docs.microsoft.com/windows/desktop/Midl/midl-command-line-reference) (Referencia de la línea de comandos de MIDL).  
  
-   **DefaultCharType**  
  
     Parámetro **String** opcional.  
  
     Especifica el tipo de carácter predeterminado que el compilador de C utilizará para compilar el código generado.  
  
     Especifique uno de los valores siguientes, cada uno de los cuales corresponde a una opción de línea de comandos.  
  
    |Valor|Opción de la línea de comandos|  
    |-----------|--------------------------|  
    |**Signed**|**/char signed**|  
    |**Unsigned**|**/char unsigned**|  
    |**Ascii**|**/char ascii7**|  
  
     Para obtener más información, vea la opción **/char** en [MIDL command-line reference](https://docs.microsoft.com/windows/desktop/Midl/midl-command-line-reference) (Referencia de la línea de comandos de MIDL).  
  
-   **DllDataFileName**  
  
     Parámetro **String** opcional.  
  
     Especifica el nombre de archivo para el archivo *dlldata* generado para una DLL de proxy.  
  
     Para obtener más información, vea la opción **/dlldata** en [MIDL command-line reference](https://docs.microsoft.com/windows/desktop/Midl/midl-command-line-reference) (Referencia de la línea de comandos de MIDL).  
  
-   **EnableErrorChecks**  
  
     Parámetro **String** opcional.  
  
     Especifica el tipo de error al comprobar que los códigos auxiliares generados funcionarán en tiempo de ejecución.  
  
     Especifique uno de los valores siguientes, cada uno de los cuales corresponde a una opción de línea de comandos.  
  
    |Valor|Opción de la línea de comandos|  
    |-----------|--------------------------|  
    |**Ninguno**|**/error none**|  
    |**EnableCustom**|**/error**|  
    |**All**|**/error all**|  
  
     Para obtener más información, vea la opción **/error** en [MIDL command-line reference](https://docs.microsoft.com/windows/desktop/Midl/midl-command-line-reference) (Referencia de la línea de comandos de MIDL).  
  
-   **ErrorCheckAllocations**  
  
     Parámetro **Boolean** opcional.  
  
     Si `true`, compruebe si hay errores de memoria insuficiente.  
  
     Para obtener más información, vea la opción **/error allocation** en [MIDL command-line reference](https://docs.microsoft.com/windows/desktop/Midl/midl-command-line-reference) (Referencia de la línea de comandos de MIDL).  
  
-   **ErrorCheckBounds**  
  
     Parámetro **Boolean** opcional.  
  
     Si `true`, comprueba el tamaño de la variable conforme y diferentes matrices con la especificación de longitud de transmisión.  
  
     Para obtener más información, vea la opción **/error bounds_check** en [MIDL command-line reference](https://docs.microsoft.com/windows/desktop/Midl/midl-command-line-reference) (Referencia de la línea de comandos de MIDL).  
  
-   **ErrorCheckEnumRange**  
  
     Parámetro **Boolean** opcional.  
  
     Si `true`, comprueba que los valores de enumeración están en un intervalo permitido.  
  
     Para obtener más información, vea la opción **/error enum** en la ayuda de la línea de comandos (**/?**) de *midl.exe*.  
  
-   **ErrorCheckRefPointers**  
  
     Parámetro **Boolean** opcional.  
  
     Si `true`, compruebe que ningún puntero de referencia nula se pasa a los códigos auxiliares del cliente.  
  
     Para obtener más información, vea la opción **/error ref** en [MIDL command-line reference](https://docs.microsoft.com/windows/desktop/Midl/midl-command-line-reference) (Referencia de la línea de comandos de MIDL).  
  
-   **ErrorCheckStubData**  
  
     Parámetro **Boolean** opcional.  
  
     Si `true`, genera un código auxiliar que detecta las excepciones de anulación del cálculo de referencias en el servidor y las propaga al cliente.  
  
     Para obtener más información, vea la opción **/error stub_data** en [MIDL command-line reference](https://docs.microsoft.com/windows/desktop/Midl/midl-command-line-reference) (Referencia de la línea de comandos de MIDL).  
  
-   **GenerateClientFiles**  
  
     Parámetro **String** opcional.  
  
     Especifica si el compilador genera archivos de origen de C del cliente para una interfaz RPC.  
  
     Especifique uno de los valores siguientes, cada uno de los cuales corresponde a una opción de línea de comandos.  
  
    |Valor|Opción de la línea de comandos|  
    |-----------|--------------------------|  
    |**Ninguno**|**/client none**|  
    |**Stub**|**/client stub**|  
  
     Para obtener más información, vea la opción **/client** en [MIDL command-line reference](https://docs.microsoft.com/windows/desktop/Midl/midl-command-line-reference) (Referencia de la línea de comandos de MIDL).  
  
-   **GenerateServerFiles**  
  
     Parámetro **String** opcional.  
  
     Especifica si el compilador genera archivos de origen de C del servidor para una interfaz RPC.  
  
     Especifique uno de los valores siguientes, cada uno de los cuales corresponde a una opción de línea de comandos.  
  
    |Valor|Opción de la línea de comandos|  
    |-----------|--------------------------|  
    |**Ninguno**|**/server none**|  
    |**Stub**|**/server stub**|  
  
     Para obtener más información, vea la opción **/server** en [MIDL command-line reference](https://docs.microsoft.com/windows/desktop/Midl/midl-command-line-reference) (Referencia de la línea de comandos de MIDL).  
  
-   **GenerateStublessProxies**  
  
     Parámetro **Boolean** opcional.  
  
     Si `true`, genera códigos auxiliares totalmente interpretados junto con servidores proxy sin código auxiliar para las interfaces de objetos.  
  
     Para obtener más información, vea la opción **/Oicf** en [MIDL command-line reference](https://docs.microsoft.com/windows/desktop/Midl/midl-command-line-reference) (Referencia de la línea de comandos de MIDL).  
  
-   **GenerateTypeLibrary**  
  
     Parámetro **Boolean** opcional.  
  
     Si es `true`, no se genera ningún archivo de biblioteca de tipos (*.tlb*).  
  
     Para obtener más información, vea la opción **/notlb** en [MIDL command-line reference](https://docs.microsoft.com/windows/desktop/Midl/midl-command-line-reference) (Referencia de la línea de comandos de MIDL).  
  
-   **HeaderFileName**  
  
     Parámetro **String** opcional.  
  
     Especifica el nombre del archivo de encabezado generado.  
  
     Para obtener más información, vea la opción **/h** o **/header** en [MIDL command-line reference](https://docs.microsoft.com/windows/desktop/Midl/midl-command-line-reference) (Referencia de la línea de comandos de MIDL).  
  
-   **IgnoreStandardIncludePath**  
  
     Parámetro **Boolean** opcional.  
  
     Si `true`, la tarea MIDL solo busca en los directorios especificados mediante el modificador **AdditionalIncludeDirectories** y omite tanto el directorio actual como los directorios especificados por la variable de entorno INCLUDE.  
  
     Para obtener más información, vea la opción **/no_def_idir** en [MIDL command-line reference](https://docs.microsoft.com/windows/desktop/Midl/midl-command-line-reference) (Referencia de la línea de comandos de MIDL).  
  
-   **InterfaceIdentifierFileName**  
  
     Parámetro **String** opcional.  
  
     Especifica el nombre del *archivo del identificador de interfaz* para una interfaz COM. Esto invalida el nombre predeterminado obtenido al agregar "_i.c" al nombre de archivo IDL.  
  
     Para obtener más información, vea la opción **/iid** en [MIDL command-line reference](https://docs.microsoft.com/windows/desktop/Midl/midl-command-line-reference) (Referencia de la línea de comandos de MIDL).  
  
-   **LocaleID**  
  
     Parámetro **int** opcional.  
  
     Especifica el *identificador de configuración regional* que habilita el uso de caracteres internacionales en archivos de entrada, nombres de archivo y rutas de acceso de directorio. Especificar un identificador de configuración regional decimal.  
  
     Para obtener más información, vea la opción **/lcid** en [MIDL command-line reference](https://docs.microsoft.com/windows/desktop/Midl/midl-command-line-reference) (Referencia de la línea de comandos de MIDL). Además, vea [Locale identifiers](https://docs.microsoft.com/windows/desktop/intl/locale-identifiers) (Identificadores de configuración regional).  
  
-   **MkTypLibCompatible**  
  
     Parámetro **Boolean** opcional.  
  
     Si es `true`, necesita que el formato del archivo de entrada sea compatible con *mktyplib.exe* versión 2.03.  
  
     Para obtener más información, vea la opción **/mktyplib203** en [MIDL command-line reference](https://docs.microsoft.com/windows/desktop/Midl/midl-command-line-reference) (Referencia de la línea de comandos de MIDL). Además, vea [ODL file syntax](/previous-versions/windows/desktop/automat/odl-file-syntax) (Sintaxis de archivos ODL) en el sitio web de MSDN.  
  
-   **OutputDirectory**  
  
     Parámetro **String** opcional.  
  
     Especifica el directorio predeterminado en que la tarea MIDL escribe los archivos de salida.  
  
     Para obtener más información, vea la opción **/out** en [MIDL command-line reference](https://docs.microsoft.com/windows/desktop/Midl/midl-command-line-reference) (Referencia de la línea de comandos de MIDL).  
  
-   **PreprocessorDefinitions**  
  
     Parámetro **String[]** opcional.  
  
     Especifica uno o más *defines*; es decir, un nombre y un valor opcional que se pasará al preprocesador de C como si lo hiciera una directiva de `#define`. El formato de cada define es *name[=value]*.  
  
     Para obtener más información, vea la opción **/D** en [MIDL command-line reference](https://docs.microsoft.com/windows/desktop/Midl/midl-command-line-reference) (Referencia de la línea de comandos de MIDL). Consulte también el parámetro **UndefinePreprocessorDefinitions** en esta tabla.  
  
-   **ProxyFileName**  
  
     Parámetro **String** opcional.  
  
     Especifica el nombre del archivo de proxy de interfaz para una interfaz COM.  
  
     Para obtener más información, vea la opción **/proxy** en [MIDL command-line reference](https://docs.microsoft.com/windows/desktop/Midl/midl-command-line-reference) (Referencia de la línea de comandos de MIDL).  
  
-   **RedirectOutputAndErrors**  
  
     Parámetro **String** opcional.  
  
     Redirige la salida, como los mensajes de error y advertencias, desde la salida estándar al archivo especificado.  
  
     Para obtener más información, vea la opción **/o** en [MIDL command-line reference](https://docs.microsoft.com/windows/desktop/Midl/midl-command-line-reference) (Referencia de la línea de comandos de MIDL).  
  
-   **ServerStubFile**  
  
     Parámetro **String** opcional.  
  
     Especifica el nombre del archivo de código auxiliar de servidor para una interfaz RPC.  
  
     Para obtener más información, vea la opción **/sstub** en [MIDL command-line reference](https://docs.microsoft.com/windows/desktop/Midl/midl-command-line-reference) (Referencia de la línea de comandos de MIDL). Consulte también el parámetro **ClientStubFile** en esta tabla.  
  
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
  
     Para obtener más información, vea la opción **/Zp** en [MIDL command-line reference](https://docs.microsoft.com/windows/desktop/Midl/midl-command-line-reference) (Referencia de la línea de comandos de MIDL). La opción **/Zp** es equivalente a la opción **/pack** y a la antigua opción **/align**.  
  
-   **SuppressCompilerWarnings**  
  
     Parámetro **Boolean** opcional.  
  
     Si `true`, suprime los mensajes de advertencia de la tarea MIDL.  
  
     Para obtener más información, vea la opción **/no_warn** en [MIDL command-line reference](https://docs.microsoft.com/windows/desktop/Midl/midl-command-line-reference) (Referencia de la línea de comandos de MIDL).  
  
-   **SuppressStartupBanner**  
  
     Parámetro `Boolean` opcional.  
  
     Si es `true`, evita que se muestre el copyright y el mensaje de número de versión cuando la tarea se inicia.   
  
     Para obtener más información, vea la opción **/nologo** en [MIDL command-line reference](https://docs.microsoft.com/windows/desktop/Midl/midl-command-line-reference) (Referencia de la línea de comandos de MIDL).  
  
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
  
     Para obtener más información, vea la opción **/env** en [MIDL command-line reference](https://docs.microsoft.com/windows/desktop/Midl/midl-command-line-reference) (Referencia de la línea de comandos de MIDL).  
  
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
  
     Para obtener más información, vea las opciones **/newtlb** y **/oldtlb** en [MIDL command-line reference](https://docs.microsoft.com/windows/desktop/Midl/midl-command-line-reference) (Referencia de la línea de comandos de MIDL).  
  
-   **TypeLibraryName**  
  
     Parámetro **String** opcional.  
  
     Especifica el nombre del archivo de biblioteca de tipos.  
  
     Para obtener más información, vea la opción **/tlb** en [MIDL command-line reference](https://docs.microsoft.com/windows/desktop/Midl/midl-command-line-reference) (Referencia de la línea de comandos de MIDL).  
  
-   **UndefinePreprocessorDefinitions**  
  
     Parámetro **String[]** opcional.  
  
     Quita cualquier definición anterior de un nombre, pasando el nombre al preprocesador de C como si lo hiciera una directiva de `#undefine`. Especifique uno o más nombres definidos previamente.  
  
     Para obtener más información, vea la opción **/U** en [MIDL command-line reference](https://docs.microsoft.com/windows/desktop/Midl/midl-command-line-reference) (Referencia de la línea de comandos de MIDL). Consulte también el parámetro **PreprocessorDefinitions** en esta tabla.  
  
-   **ValidateAllParameters**  
  
     Parámetro `Boolean` opcional.  
  
     Si `true`, genera información de comprobación de errores adicional que se utiliza para realizar comprobaciones de integridad en tiempo de ejecución. Si `false`, no se genera la información de comprobación de errores.  
  
     Para obtener más información, vea las opciones **/robust** y **/no_robust** en [MIDL command-line reference](https://docs.microsoft.com/windows/desktop/Midl/midl-command-line-reference) (Referencia de la línea de comandos de MIDL).  
  
-   **WarnAsError**  
  
     Parámetro `Boolean` opcional.  
  
     Si `true`, trata todas las advertencias como errores.  
  
     Si no se especifica el parámetro de la tarea MIDL **WarningLevel**, las advertencias del nivel 1, el nivel predeterminado, se tratan como errores.  
  
     Para obtener más información, vea las opciones **/WX** en [MIDL command-line reference](https://docs.microsoft.com/windows/desktop/Midl/midl-command-line-reference) (Referencia de la línea de comandos de MIDL). Consulte también el parámetro **WarningLevel** en esta tabla.  
  
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
  
     Para obtener más información, vea la opción **/W** en [MIDL command-line reference](https://docs.microsoft.com/windows/desktop/Midl/midl-command-line-reference) (Referencia de la línea de comandos de MIDL). Consulte también el parámetro **WarnAsError** en esta tabla.  
  
## <a name="see-also"></a>Vea también  
 [Referencia de tareas](../msbuild/msbuild-task-reference.md)