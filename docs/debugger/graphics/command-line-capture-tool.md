---
title: Herramienta de línea de comandos de captura | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: db75b3a7-80b2-4a74-91d2-fd6e0f73b45d
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7b5de323a14bd005e10db4c17281a3b947381f26
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/05/2018
ms.locfileid: "43775563"
---
# <a name="command-line-capture-tool"></a>Herramienta de captura de línea de comandos
DXCap.exe es una herramienta de línea de comandos para la captura y la reproducción de diagnóstico de gráficos. Admite Direct3D 10 a través de Direct3D 12 en todos los niveles de características.  
  
## <a name="syntax"></a>Sintaxis  
  
```cmd  
DXCap.exe [-file filename] [-frame frames | -period periods | -manual] -c app [args...]  
DXCap.exe -p [filename] [-debug | -warp | -hw] [-config] [-rawmode]  
DXCap.exe -p [filename] -screenshot [-frame frames]  
DXCap.exe -p [filename] -toXML [xml_filename]  
DXCap.exe -v [-file filename] [-examine events] [-haltonfail | -exitonfail] [-showprogress]  
DXCap.exe -e [search_string]  
DXCap.exe -info  
```  
  
#### <a name="parameters"></a>Parámetros  
 `-file` `filename`  
 En el modo de captura (`-c`), `filename` especifica el nombre del archivo de registro de gráficos que se registra la información de gráficos en. Si `filename` no se especifica, se registra información de gráficos en un archivo denominado `<appname>-<date>-<time>.vsglog` de forma predeterminada.  
  
 En el modo de validación (-v), `filename` especifica el nombre del archivo de registro de gráficos que se validará. Si `filename` no se especifica, se vuelve a usar el registro de gráficos que se validó por última vez.  
  
 `-frame` `frames`  
 En el modo de captura, `frames` especifica los fotogramas que quiere capturar. El primer fotograma es 1. Puede especificar varios fotogramas con comas e intervalos. Por ejemplo, si `frames` es `2, 5, 7-9, 15`, a continuación, los marcos `2`, `5`, `7`, `8`, `9`, y `15` se capturan.  

> [!TIP]
> Use `-frame` `manual` para especificar que fotogramas se capturarán manualmente presionando la tecla Impr Pant. Se pueden capturar fotogramas cuando se inicia la aplicación. Para detener la captura de fotogramas, vuelva a la interfaz de la línea de comandos y presione ENTRAR.  
  
 `-period` `periods`  
 En el modo de captura, `periods` especifica los intervalos de tiempo, en segundos, durante los cuales quiere capturar fotogramas. Puede especificar varios períodos con comas e intervalos. Por ejemplo si `periods` es `2.1-5, 7.0-9.3`, fotogramas que se representan entre `2.1` y `5` segundos y entre`7` y `9.3` segundos se capturan.  
  
 `-c` `app` [`args...`]  
 Modo de captura. En el modo de captura, `app` especifica el nombre de la aplicación de cuyos gráficos quiere capturar información. `args...` especifica los parámetros de línea de comandos adicionales para esa aplicación.  
  
 `-p` [`filename`]  
 Modo de reproducción (`-p`). En el modo de reproducción, `filename` especifica el nombre del archivo de registro de gráficos que se reproducirá. Si `filename` no se especifica, se vuelve a usar el registro de gráficos por última vez reproducido.  
  
 `-debug`  
 En el modo de reproducción, `-debug` especifica que la reproducción se debe reproducir con la capa de depuración de Direct3D habilitada.  
  
 `-warp`  
 En el modo de reproducción, `-warp` especifica que la reproducción se debe reproducir mediante el representador de software WARP.  
  
 `-hw`  
 En el modo de reproducción, `-hw` especifica que la reproducción se debe reproducir con hardware de GPU.  
  
 `-config`  
 En el modo de reproducción, `-config` muestra toda la información sobre la máquina que se usó para capturar el archivo de registro de gráficos.  
  
 `-rawmode`  
 En el modo de reproducción, `-rawmode` especifica que la reproducción debe realizarse sin modificar los eventos registrados. Con un funcionamiento normal, es posible que el modo de reproducción realice pequeños cambios en la reproducción para simplificar la depuración y agilizar la reproducción. Por ejemplo, puede que simule la salida de la cadena de intercambio, en lugar de ejecutar los comandos de la cadena de intercambio. Normalmente esta reproducción no es un problema, pero puede necesitar la reproducción se realice de manera más fiel al evento registrado. Por ejemplo, puede usar esta opción para restaurar el comportamiento de representación de pantalla completa en una aplicación que se capturó mientras se ejecuta en modo de pantalla completa.  
  
 `-toXML` [`xml_filename`]  
 En el modo de reproducción, `xml_filename` especifica el nombre del archivo donde se escribe una representación XML de la reproducción. Si no se especifica `xml_filename`, la representación XML se escribe en un archivo con el mismo nombre que el del archivo que se reproduce, pero con la extensión `.xml`.  
  
 `-v`  
 Modo de validación. En el modo de validación, los fotogramas capturados se reproducen en hardware y en WARP y sus resultados se comparan con una función de comparación de imágenes. Puede utilizar esta característica para identificar rápidamente problemas de controladores que afecten a la representación.  
  
 `-examine` `events`  
 En el modo de validación, `events` especifica el conjunto de eventos de gráficos cuyos resultados inmediatos se comparan. Por ejemplo, `-examine present,draw,copy,clear` limita la comparación para que solo los eventos que pertenecen a esas categorías.  
  
> [!TIP]
>  Se recomienda empezar por `-examine present,draw,copy,clear` porque se revela la mayoría de los problemas pero significativamente más rápido que un conjunto más amplio de eventos. Si es necesario, puede especificar un conjunto de eventos mayor o distinto para validar los eventos y mostrar otros tipos de problemas.  
  
 `-haltonfail`  
 En el modo de validación, `-haltonfail` detiene la validación cuando se detectan las diferencias entre el hardware y el representador WARP. La validación se reanuda al presionar una tecla.  
  
 `-exitonfail`  
 En el modo de validación, `-exitonfail` sale validación inmediatamente cuando se detectan las diferencias entre el hardware y el representador WARP. Cuando se cierra el programa de esta manera, devuelve `0` al entorno; de lo contrario, devuelve `1`.  
  
 `-showprogress`  
 En el modo de validación, `-showprogress` muestra información de progreso de la sesión de validación. El progreso de WARP se muestra a la izquierda y el progreso de hardware se muestra a la derecha.  
  
 `-e` `search_string`  
 Enumera las aplicaciones UWP que se instalan. Puede usar esta información para realizar capturas de línea de comandos con aplicaciones para UWP.  
  
 `-info`  
 Muestra información sobre las DLL de captura y de máquina.  
  
## <a name="remarks"></a>Comentarios  
 DXCap.exe funciona en tres modos:  
  
 Modo de captura (-c)  
 Capturar información de gráficos de una aplicación en ejecución y registrarla en un archivo de registro de gráficos. Las funcionalidades de captura y el formato de archivo son idénticos a los de Visual Studio.  
  
 Modo de reproducción (-p)  
 Reproducción ha capturado previamente los eventos de gráficos desde un archivo de registro de gráficos existente. De forma predeterminada, la reproducción se realiza en una ventana, aunque el archivo de registro de gráficos se capturara desde una aplicación de pantalla completa. Se produce la reproducción en la pantalla completa solo cuando el registro de gráficos se capturó archivo desde una aplicación de pantalla completa y `-rawmode` se especifica.  
  
 Modo de validación (`-v`)  
 Valida el comportamiento de representación reproduciendo los fotogramas capturados en hardware y en WARP y, luego, comparando los resultados con una función de comparación de imágenes. Puede utilizar esta característica para identificar rápidamente problemas de controladores que afecten a la representación.  
  
 Además de estos modos, dxcap.exe realiza otras dos funciones que no capturan ni reproducen información de gráficos.  
  
 Función de enumeración (`-e`)  
 Muestra detalles acerca de las aplicaciones UWP que se instalan en el equipo. Estos detalles incluyen el nombre del paquete y el appid que identifican el archivo ejecutable en una aplicación para UWP. Para capturar información de gráficos desde una aplicación de la Tienda Windows con DXCap.exe, utilice el nombre del paquete y el appid en lugar del nombre del archivo ejecutable que se usa al capturar una aplicación de escritorio.  
  
 (Función de información`-info)`  
 Muestra detalles sobre las DLL de captura y de máquina.  
  
## <a name="examples"></a>Ejemplos  
  
### <a name="capture-graphics-information-from-a-desktop-app"></a>Captura de información de gráficos desde una aplicación de escritorio  
 Use `-c` para especificar la aplicación desde el que desea capturar información de gráficos.  
  
```cmd  
DXCap.exe -c BasicHLSL11.exe  
```  
  
 De forma predeterminada, la información de gráficos se registra en un archivo denominado `<appname>-<date>-<time>.vsglog`. Use `-file` para especificar un archivo diferente donde quiera registrar.  
  
```cmd  
DXCap.exe -file regression_test_12.vsglog -c BasicHLSL11.exe  
```  
  
 Especifique los parámetros de línea de comandos adicionales para la aplicación de la que está realizando la captura incluyéndolos después del nombre de archivo de la aplicación.  
  
```cmd  
DXCap.exe -c "C:\Program Files\Internet Explorer\iexplorer.exe" "www.fishgl.com"  
```  
  
 El comando en el ejemplo anterior captura la información de gráficos desde la versión de escritorio de Internet Explorer durante la visualización de la página Web ubicada en www.fishgl.com que usa la API WebGL para representar contenido 3D.  
  
> [!NOTE]
>  Dado que se pasan los argumentos de línea de comandos que aparecen después de la aplicación, debe especificar los argumentos destinados a DXCap.exe antes de usar el `-c` opción.  
  
### <a name="capture-graphics-information-from-a-uwp-app"></a>Capturar información gráfica desde una aplicación para UWP.  
 Puede capturar información de gráficos desde una aplicación para UWP.  
  
```cmd  
DXCap.exe -c Microsof.BingMaps_2.1.2914.1734_x64__8wekyb3d8bbwe,AppexMaps  
```  
  
 Usar DXCap.exe para capturar desde una aplicación para UWP es parecido a usarlo para capturar desde una aplicación de escritorio de Windows, pero en su lugar que identifica una aplicación de escritorio por su nombre de archivo, identifica una aplicación para UWP por su nombre de paquete y el nombre o Id. de lo ejecutable dentro del paquete que quiere  captura de. Para que sea más fácil de obtener información sobre cómo identificar las aplicaciones UWP que se instalan en el equipo, use el `-e` opción con DXCap.exe para enumerarlas:  
  
```cmd  
DXCap.exe -e  
```  
  
 Puede proporcionar una cadena de búsqueda opcional para buscar más fácilmente la aplicación que está buscando. Cuando se proporciona la cadena de búsqueda, DXCap.exe enumera las aplicaciones UWP cuyo nombre de paquete, nombre de la aplicación o Id. de aplicación coincide con la cadena de búsqueda. La búsqueda no distingue entre mayúsculas y minúsculas.  
  
```cmd  
DXCap.exe -e map  
```  
  
 El comando anterior enumera las aplicaciones para UWP que coinciden con "map"; Este es el resultado:  
  
 **Paquete "Microsoft.BingMaps":**  
 **InstallDirectory: C:\Program Files\WindowsApps\Microsoft.BingMaps_2.1.2914.1734_x64__8wekyb3d8bbwe**  
 **FullName: Microsoft.BingMaps_2.1.2914.1734_x64__8wekyb3d8bbwe**  
 **UserSID: S-1-5-21-2127521184-1604012920-1887927527-5603533**  
 **Nombre: Microsoft.BingMaps**  
 **Publicador: CN = Microsoft Corporation, O = Microsoft Corporation, L = Redmond, S = Washington, C = US**  
 **Versión: 2.1.2914.1734**  
 **Aplicaciones que se pueda iniciar:**  
 **Id.: AppexMaps**  
 **Exe: C:\Program Files\WindowsApps\Microsoft.BingMaps_2.1.2914.1734_x64__8wekyb3d8bbwe\Map.exe**  
 **IsWWA: N**  
 **AppSpec (para iniciar): DXCap.exe - c Microsoft.BingMaps_2.1.2914.1734_x64__8wekyb3d8bbwe,AppexMaps** la última línea de salida para cada aplicación enumerada muestra el comando puede utilizar para capturar información de gráficos.  
  
### <a name="capture-specific-frames-or-frames-between-specific-times"></a>Capturar fotogramas específicos o fotogramas entre momentos específicos.  
 Use `-frame` para especificar los fotogramas que desee capturar con comas e intervalos:  
  
```cmd  
DXCap.exe -frame 2,5,7-9,15 -c SimpleBezier11.exe  
```  
  
 O bien, use `-period` para especificar un conjunto de intervalos de tiempo durante el que se va a capturar fotogramas. Los intervalos de tiempo se especifican en segundos y se pueden especificar varios intervalos:  
  
```cmd  
DXCap.exe -period 2.1-5, 7.0-9.3 -c SimpleBezier11.exe  
```  
  
### <a name="capture-frames-interactively"></a>Capturar fotogramas de forma interactiva.  
 Use `-manual` para capturar fotogramas de forma interactiva. Presione la tecla ENTRAR para iniciar la captura y vuelva a presionar la tecla ENTRAR para detenerla.  
  
```cmd  
DXCap.exe -manual -c SimpleBezier11.exe  
```  
  
### <a name="play-back-a-graphic-log-file"></a>Reproducir un archivo de registro de gráficos  
 Use `-p` para reproducir un archivo de registro de gráficos capturada previamente.  
  
```cmd  
DXCap.exe -p regression_test_12.vsglog  
```  
  
 Si quiere reproducir el último registro de gráficos que se capturó, omita el nombre de archivo.  
  
```cmd  
DXCap.exe -p  
```  
  
### <a name="play-back-in-raw-mode"></a>Reproducción en modo sin procesar  
 Use `-rawmode` para reproducir los comandos capturados exactamente como se produjeron. En el modo de reproducción normal, algunos comandos se emulan: por ejemplo, un archivo de registro de gráficos capturado a partir de una aplicación de pantalla completa se ejecuta en una ventana. Con el modo sin procesar habilitado, el mismo archivo tratará de reproducirse a pantalla completa.  
  
```cmd  
DXCap.exe -p regression_test_12.vsglog -rawmode  
```  
  
### <a name="play-back-using-warp-or-a-hardware-device"></a>Reproducción con WARP o con un dispositivo de hardware  
 Puede que quiera forzar la reproducción de un archivo de registro de gráficos capturado en un dispositivo de hardware para usar WARP, o forzar la reproducción de un registro capturado en WARP para usar un dispositivo de hardware. Use `-warp` para reproducir con WARP.  
  
```cmd  
DXCap.exe -p regression_test_12.vsglog -warp  
```  
  
 Use `-hw` para reproducir con hardware.  
  
```cmd  
DXCap.exe -p regression_test_12.vsglog -hw  
```  
  
### <a name="validate-a-graphics-log-file-against-warp"></a>Validación de un archivo de registro de gráficos con WARP  
 En el modo de validación, el archivo de registro de gráficos se reproduce en hardware y en WARP y se comparan los resultados. Así, es más fácil identificar los errores de representación provocados por el controlador. Use - v para validar el comportamiento correcto de hardware de gráficos con WARP.  
  
```cmd  
DXCap.exe -v regression_test_12.vsglog  
```  
  
 Para reducir la cantidad de comparaciones, puede especificar un subconjunto de comandos de validación que quiera comparar, y los demás comandos se pasarán por alto. Use - Examinar para especificar los comandos cuyos resultados desea comparar.  
  
```cmd  
DXCap.exe -v regression_test_12.vsglog -examine present,draw,copy,clear  
```  
  
### <a name="convert-a-graphics-log-file-to-pngs"></a>Conversión de un archivo de registro de gráficos en archivos PNG  
 Para ver o analizar los fotogramas de un archivo de registro de gráficos, DXCap.exe puede guardar fotogramas capturados como archivos de imagen .png (Portable Network Graphics). Use `-screenshot` a en el modo de reproducción para generar los fotogramas capturados como archivos. png.  
  
```cmd  
DXCap.exe -p BasicHLSL11.vsglog -screenshot  
```  
  
 Use `-frame` con `-screenshot` para especificar los fotogramas que desee para la salida.  
  
```cmd  
DXCap.exe -p BasicHLSL11.vsglog -screenshot -frame 5, 7-9  
```  
  
### <a name="convert-a-graphics-log-file-to-xml"></a>Conversión de un archivo de registro de gráficos a XML  
 Para procesar y analizar los registros de gráficos con herramientas conocidas, como FindStr o XSLT, DXCap.exe puede convertir un archivo de registro de gráficos a XML. Use `-toXML` en modo de reproducción para convertir el registro a XML en lugar de reproducirlo realizar una copia.  
  
```cmd  
DXCap.exe -p regression_test_12.vsglog -toXML  
```  
  
 De manera predeterminada, el XML resultante se escribe en un archivo con el mismo nombre que el del registro de gráficos, pero con la extensión .xml. En el ejemplo anterior, el archivo XML se denominará **regression_test_12.xml**. Para asignar el archivo XML de un nombre diferente, especifíquelo después `-toXML`.  
  
```cmd  
DXCap.exe -p regression_test_12.vsglog -toXML temp.xml  
```  
  
 El archivo resultante contendrá XML con un aspecto similar a este:  
  
```xml  
<Moment value="67"/>  
<Method name="CreateDXGIFactory1" >  
    <Return type="HRESULT" value="S_OK" />  
    <Parameter name="riid" type="IID" value="770AAE78-F26F-4DBA-A829-253C83D1B387" />  
    <Parameter name="ppFactory" type="void" handle="1" isOutput="true" />  
</Method>  
  
<Moment value="167"/>  
<Method name="D3D11CreateDevice" >  
    <Return type="HRESULT" value="S_OK" />  
    <Parameter name="pAdapter" type="IDXGIAdapter" handle="34" />  
    <Parameter name="DriverType" type="D3D_DRIVER_TYPE" value="D3D_DRIVER_TYPE_UNKNOWN" />  
    <Parameter name="Software" type="HMODULE" value="pointer" />  
    <Parameter name="Flags" type="UINT" value="0" />  
    <Parameter name="pFeatureLevels" type="D3D_FEATURE_LEVEL" arrSize="1" >  
        <Element value="D3D_FEATURE_LEVEL_11_0" />  
    </Parameter>  
    <Parameter name="FeatureLevels" type="UINT" value="1" />  
    <Parameter name="SDKVersion" type="UINT" value="7" />  
    <Parameter name="ppDevice" type="ID3D11Device" handle="35" isOutput="true" />  
    <Parameter name="pFeatureLevel" type="D3D_FEATURE_LEVEL" value="D3D_FEATURE_LEVEL_11_0" isOutput="true" />  
    <Parameter name="ppImmediateContext" type="ID3D11DeviceContext" value="nullptr" isOutput="true" />  
</Method>  
```  
  
## <a name="requirements"></a>Requisitos