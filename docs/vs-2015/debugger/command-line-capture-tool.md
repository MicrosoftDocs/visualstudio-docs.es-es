---
title: Herramienta de captura de línea de comandos | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: db75b3a7-80b2-4a74-91d2-fd6e0f73b45d
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 208ff7f9bbfc2d07669a8b485edffc8dfc4cd54f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "90842862"
---
# <a name="command-line-capture-tool"></a>Herramienta de captura de línea de comandos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

DXCap.exe es una herramienta de línea de comandos para la captura y la reproducción de diagnóstico de gráficos. Admite Direct3D 10 a través de Direct3D 12 en todos los niveles de características.  
  
## <a name="syntax"></a>Sintaxis  
  
```ms-dos  
DXCap.exe [-file filename] [-frame frames | -period periods | -manual] -c app [args...]  
DXCap.exe -p [filename] [-debug | -warp | -hw] [-config] [-rawmode]  
DXCap.exe –p [filename] –screenshot [-frame frames]  
DXCap.exe –p [filename] –toXML [xml_filename]  
DXCap.exe –v [–file filename] [-examine events] [-haltonfail | -exitonfail] [-showprogress]  
DXCap.exe -e [search_string]  
DXCap.exe –info  
```  
  
#### <a name="parameters"></a>Parámetros  
 `-file` `filename`  
 : en el modo de captura (`-c`), `filename` especifica el nombre del archivo de registro de gráficos en el que se registra la información de los gráficos. Si `filename` no se especifica, la información de los gráficos se registra en un archivo denominado `<appname>-<date>-<time>.vsglog` de forma predeterminada.  
  
 En el modo de validación (-v), `filename` especifica el nombre del archivo de registro de gráficos que se validará. Si no se especifica `filename`, se usará otra vez el último registro de gráficos que se validó.  
  
 `-frame` `frames`  
 En el modo de captura, `frames` especifica los fotogramas que quiere capturar. El primer fotograma es 1. Puede especificar varios fotogramas con comas e intervalos. Por ejemplo, si `frames` es `2, 5, 7-9, 15`, entonces se capturan los fotogramas `2`, `5`, `7`, `8`, `9` y `15`.  
  
 `-period` `periods`  
 En el modo de captura, `periods` especifica los intervalos de tiempo, en segundos, durante los cuales quiere capturar fotogramas. Puede especificar varios períodos con comas e intervalos. Por ejemplo, si `periods` es `2.1-5, 7.0-9.3`, entonces se capturan los fotogramas que se representan entre `2.1` y `5` segundos, y entre`7` y `9.3` segundos.  
  
 `-manual`  
 En modo de captura, `-manual` especifica que los fotogramas se capturarán manualmente presionando la tecla Impr Pant. Se pueden capturar fotogramas cuando se inicia la aplicación. Para detener la captura de fotogramas, vuelva a la interfaz de la línea de comandos y presione ENTRAR.  
  
 `-c` `app` [`args...`]  
 Modo de captura. En el modo de captura, `app` especifica el nombre de la aplicación de cuyos gráficos quiere capturar información. `args...` especifica los parámetros de línea de comandos adicionales para esa aplicación.  
  
 `-p` [`filename`]  
 Modo de reproducción ( `-p` ). En el modo de reproducción, `filename` especifica el nombre del archivo de registro de gráficos que se reproducirá. Si no se especifica `filename`, se usará otra vez el último registro de gráficos que se reprodujo.  
  
 `-debug`  
 En el modo de reproducción, `-debug` especifica que la reproducción se debe realizar con la capa de depuración de Direct3D habilitada.  
  
 `-warp`  
 En el modo de reproducción, `-warp` especifica que la reproducción debe realizarse con el representador de dewarp software.  
  
 `-hw`  
 En el modo de reproducción, `-hw` especifica que la reproducción debe realizarse mediante hardware de GPU.  
  
 `-config`  
 En el modo de reproducción, `-config` muestra información sobre la máquina que se usó para capturar el archivo de registro de gráficos, si esta información se grabó en el registro.  
  
 `-rawmode`  
 : en el modo de reproducción, `-rawmode` especifica que la reproducción debe realizarse sin modificar los eventos grabados. Con un funcionamiento normal, es posible que el modo de reproducción realice pequeños cambios en la reproducción para simplificar la depuración y agilizar la reproducción. Por ejemplo, puede que simule la salida de la cadena de intercambio, en lugar de ejecutar los comandos de la cadena de intercambio. En general, esto no es un problema, pero tal vez necesite que la reproducción se realice de una manera más fiel a los eventos grabados. Por ejemplo, puede utilizar esta opción para restaurar el comportamiento de representación de pantalla completa en una aplicación que se capturó mientras se ejecutaba en modo de pantalla completa.  
  
 `-toXML` [`xml_filename`]  
 En el modo de reproducción, `xml_filename` especifica el nombre del archivo donde se escribe una representación XML de la reproducción. Si no se especifica `xml_filename`, la representación XML se escribe en un archivo con el mismo nombre que el del archivo que se reproduce, pero con la extensión `.xml`.  
  
 `-v`  
 Modo de validación. En el modo de validación, los fotogramas capturados se reproducen en hardware y en WARP y sus resultados se comparan con una función de comparación de imágenes. Puede utilizar esta característica para identificar rápidamente problemas de controladores que afecten a la representación.  
  
 `-examine` `events`  
 En el modo de validación, `events` especifica el conjunto de eventos de gráficos cuyos resultados inmediatos se comparan. Por ejemplo, `-examine present,draw,copy,clear` limita la comparación a solo los eventos que pertenecen a esas categorías.  
  
> [!TIP]
> Se recomienda empezar por `-examine present,draw,copy,clear`, ya que esto revela la mayoría de los problemas, pero es considerablemente más rápido que un conjunto de eventos más amplio. Si es necesario, puede especificar un conjunto de eventos mayor o distinto para validar los eventos y mostrar otros tipos de problemas.  
  
 `-haltonfail`  
 : en el modo de validación, `-haltonfail` detiene la validación cuando se encuentran diferencias entre el representador de hardware y WARP. La validación se reanuda al presionar una tecla.  
  
 `-exitonfail`  
 : en el modo de validación, `-exitonfail` sale inmediatamente de la validación cuando se encuentran diferencias entre el representador de hardware y WARP. Si el programa sale de esta manera, devuelve `0` al entorno. Si no, devuelve `1`.  
  
 `-showprogress`  
 : en el modo de validación, `-showprogress` muestra la información de progreso de la sesión de validación. El progreso de WARP se muestra a la izquierda y el progreso de hardware se muestra a la derecha.  
  
 `-e` `search_string`  
 Enumera las aplicaciones de la Tienda Windows que están instaladas. Puede utilizar esta información para realizar capturas de línea de comandos con las aplicaciones de la Tienda Windows.  
  
 `-info`  
 Muestra información sobre las DLL de captura y de máquina.  
  
## <a name="remarks"></a>Comentarios  
 DXCap.exe funciona en tres modos:  
  
 Modo de captura (-c)  
 Capturar información de gráficos de una aplicación en ejecución y registrarla en un archivo de registro de gráficos. Las funcionalidades de captura y el formato de archivo son idénticos a los de Visual Studio.  
  
 Modo de reproducción (-p)  
 Reproducir eventos de gráficos capturados anteriormente a partir de un archivo de registro de gráficos existente. De forma predeterminada, la reproducción se realiza en una ventana, aunque el archivo de registro de gráficos se capturara desde una aplicación de pantalla completa. La reproducción solo se produce en pantalla completa si el archivo de registro de gráficos se capturó desde una aplicación de pantalla completa y se especifica `–rawmode`.  
  
 Modo de validación (`-v`)  
 Valida el comportamiento de representación reproduciendo los fotogramas capturados en hardware y en WARP y, luego, comparando los resultados con una función de comparación de imágenes. Puede utilizar esta característica para identificar rápidamente problemas de controladores que afecten a la representación.  
  
 Además de estos modos, dxcap.exe realiza otras dos funciones que no capturan ni reproducen información de gráficos.  
  
 Función de enumeración ( `-e` )  
 Muestra detalles sobre las aplicaciones de la Tienda Windows que están instaladas en la máquina. Entre estos detalles se incluyen el nombre del paquete y el appid que identifican el archivo ejecutable en una aplicación de la Tienda Windows. Para capturar información de gráficos desde una aplicación de la Tienda Windows con DXCap.exe, utilice el nombre del paquete y el appid en lugar del nombre del archivo ejecutable que se usa al capturar una aplicación de escritorio.  
  
 Función info (`-info)`  
 Muestra detalles sobre las DLL de captura y de máquina.  
  
## <a name="examples"></a>Ejemplos  
  
### <a name="capture-graphics-information-from-a-desktop-app"></a>Captura de información de gráficos desde una aplicación de escritorio  
 Use `–c` para especificar la aplicación desde la que quiere capturar información de gráficos.  
  
```ms-dos  
DXCap.exe –c BasicHLSL11.exe  
```  
  
 De forma predeterminada, la información de los gráficos se registra en un archivo llamado `<appname>-<date>-<time>.vsglog`. Use `–file` para especificar otro archivo donde quiera registrar la información.  
  
```ms-dos  
DXCap.exe –file regression_test_12.vsglog –c BasicHLSL11.exe  
```  
  
 Especifique los parámetros de línea de comandos adicionales para la aplicación de la que está realizando la captura incluyéndolos después del nombre de archivo de la aplicación.  
  
```ms-dos  
DXCap.exe –c "C:\Program Files\Internet Explorer\iexplorer.exe" "www.fishgl.com"  
```  
  
 El comando del ejemplo anterior captura la información de los gráficos de la versión de escritorio de Internet Explorer mientras se ve la página web ubicada en www.fishgl.com, que utiliza la API WebGL para representar contenido en 3D.  
  
> [!NOTE]
> Dado que se le pasan los argumentos de línea de comandos que aparecen después de la aplicación, debe especificar los argumentos destinados a DXCap.exe antes de utilizar la opción `–c`.  
  
### <a name="capture-graphics-information-from-a-windows-store-app"></a>Capturar información de gráficos de una aplicación de la Tienda Windows.  
 Puede capturar información de gráficos de una aplicación de la Tienda Windows.  
  
```ms-dos  
DXCap.exe –c Microsof.BingMaps_2.1.2914.1734_x64__8wekyb3d8bbwe,AppexMaps  
```  
  
 Usar DXCap.exe para realizar la captura desde una aplicación de la Tienda Windows es similar a usarlo para realizar la captura desde una aplicación de escritorio de Windows, con una diferencia: las aplicaciones de escritorio se identifican por su nombre de archivo, pero las aplicaciones de la Tienda Windows se identifican por su nombre de paquete y el nombre o identificador del ejecutable que hay dentro del paquete desde el cual quiere realizar la captura. Para que sea más fácil averiguar cómo identificar las aplicaciones de la tienda Windows que están instaladas en el equipo, use la `–e` opción con DXCap.exe para enumerarlas:  
  
```ms-dos  
DXCap.exe -e  
```  
  
 Puede proporcionar una cadena de búsqueda opcional para buscar más fácilmente la aplicación que está buscando. Cuando se proporciona la cadena de búsqueda, DXCap.exe enumera las aplicaciones de la Tienda Windows cuyo nombre de paquete, nombre de aplicación o identificador de aplicación coincide con la cadena de búsqueda. La búsqueda no distingue entre mayúsculas y minúsculas.  
  
```ms-dos  
DXCap.exe –e map  
```  
  
 El comando anterior enumera las aplicaciones de la Tienda Windows que coinciden con “map”. Este es el resultado:  
  
 **Paquete "Microsoft.BingMaps":**  
 **InstallDirectory : C:\Program Files\WindowsApps\Microsoft.BingMaps_2.1.2914.1734_x64__8wekyb3d8bbwe**  
 **FullName         : Microsoft.BingMaps_2.1.2914.1734_x64__8wekyb3d8bbwe**  
 **UserSID          : S-1-5-21-2127521184-1604012920-1887927527-5603533**  
 **Nombre             : Microsoft.BingMaps**  
 **Publisher        : CN=Microsoft Corporation, O=Microsoft Corporation, L=Redmond, S=Washington, C=US**  
 **Versión          : 2.1.2914.1734**  
 **Aplicaciones disponibles:**  
 **Id   : AppexMaps**  
 **Exe  : C:\Program Files\WindowsApps\Microsoft.BingMaps_2.1.2914.1734_x64__8wekyb3d8bbwe\Map.exe**  
 **IsWWA: No**  
 **AppSpec (para iniciar): DXCap.exe-c Microsoft. BingMaps_2.1.2914.1734_x64__8wekyb3d8bbwe, AppexMaps** La última línea de la salida de cada aplicación enumerada muestra el comando que puede usar para capturar información de gráficos de ella.  
  
### <a name="capture-specific-frames-or-frames-between-specific-times"></a>Capturar fotogramas específicos o fotogramas entre momentos específicos.  
 Use `–frame` para especificar los fotogramas que quiere capturar con comas e intervalos:  
  
```ms-dos  
DXCap.exe –frame 2,5,7-9,15 –c SimpleBezier11.exe  
```  
  
 O bien, use `–period` para especificar un conjunto de intervalos de tiempo durante los cuales quiere capturar fotogramas. Los intervalos de tiempo se especifican en segundos y se pueden especificar varios intervalos:  
  
```ms-dos  
DXCap.exe –period 2.1-5, 7.0-9.3 –c SimpleBezier11.exe  
```  
  
### <a name="capture-frames-interactively"></a>Capturar fotogramas de forma interactiva.  
 Use `–manual` para capturar fotogramas de forma interactiva. Presione la tecla ENTRAR para iniciar la captura y vuelva a presionar la tecla ENTRAR para detenerla.  
  
```ms-dos  
DXCap.exe –manual -c SimpleBezier11.exe  
```  
  
### <a name="play-back-a-graphics-log-file"></a>Reproducción de un archivo de registro de gráficos  
 Use `-p` para reproducir un archivo de registro de gráficos capturado anteriormente.  
  
```ms-dos  
DXCap.exe –p regression_test_12.vsglog  
```  
  
 Si quiere reproducir el último registro de gráficos que se capturó, omita el nombre de archivo.  
  
```ms-dos  
DXCap.exe –p  
```  
  
### <a name="play-back-in-raw-mode"></a>Reproducción en modo sin procesar  
 Use `-rawmode` para reproducir los comandos capturados exactamente como se produjeron. En el modo de reproducción normal, algunos comandos se emulan: por ejemplo, un archivo de registro de gráficos capturado a partir de una aplicación de pantalla completa se ejecuta en una ventana. Con el modo sin procesar habilitado, el mismo archivo tratará de reproducirse a pantalla completa.  
  
```ms-dos  
DXCap.exe –p regression_test_12.vsglog -rawmode  
```  
  
### <a name="play-back-using-warp-or-a-hardware-device"></a>Reproducción con WARP o con un dispositivo de hardware  
 Puede que quiera forzar la reproducción de un archivo de registro de gráficos capturado en un dispositivo de hardware para usar WARP, o forzar la reproducción de un registro capturado en WARP para usar un dispositivo de hardware. Use `-warp` para realizar la reproducción con WARP.  
  
```ms-dos  
DXCap.exe –p regression_test_12.vsglog -warp  
```  
  
 Use `-hw` para realizar la reproducción con hardware.  
  
```ms-dos  
DXCap.exe –p regression_test_12.vsglog -hw  
```  
  
### <a name="validate-a-graphics-log-file-against-warp"></a>Validación de un archivo de registro de gráficos con WARP  
 En el modo de validación, el archivo de registro de gráficos se reproduce en hardware y en WARP y se comparan los resultados. Así, es más fácil identificar los errores de representación provocados por el controlador. Use –v para validar el comportamiento del hardware de gráficos en comparación con WARP y comprobar si es correcto.  
  
```ms-dos  
DXCap.exe -v regression_test_12.vsglog  
```  
  
 Para reducir la cantidad de comparaciones, puede especificar un subconjunto de comandos de validación que quiera comparar, y los demás comandos se pasarán por alto. Use –examine para especificar los comandos cuyos resultados quiere comparar.  
  
```ms-dos  
DXCap.exe -v regression_test_12.vsglog –examine present,draw,copy,clear  
```  
  
### <a name="convert-a-graphics-log-file-to-pngs"></a>Conversión de un archivo de registro de gráficos en archivos PNG  
 Para ver o analizar los fotogramas de un archivo de registro de gráficos, DXCap.exe puede guardar fotogramas capturados como archivos de imagen .png (Portable Network Graphics). Use `-screenshot` en el modo de reproducción para obtener los fotogramas capturados como archivos .png.  
  
```ms-dos  
DXCap.exe -p BasicHLSL11.vsglog -screenshot  
```  
  
 Use `–frame` con `–screenshot` para especificar los fotogramas que quiere generar.  
  
```ms-dos  
DXCap.exe -p BasicHLSL11.vsglog -screenshot –frame 5, 7-9  
```  
  
### <a name="convert-a-graphics-log-file-to-xml"></a>Conversión de un archivo de registro de gráficos a XML  
 Para procesar y analizar los registros de gráficos con herramientas conocidas, como FindStr o XSLT, DXCap.exe puede convertir un archivo de registro de gráficos a XML. Use `-toXML` en el modo de reproducción para convertir el registro a XML en lugar de reproducirlo.  
  
```ms-dos  
DXCap.exe –p regression_test_12.vsglog –toXML  
```  
  
 De manera predeterminada, el XML resultante se escribe en un archivo con el mismo nombre que el del registro de gráficos, pero con la extensión .xml. En el ejemplo anterior, el archivo XML se denominará **regression_test_12.xml**. Para asignar otro nombre al archivo XML, especifíquelo después de `-toXML`.  
  
```ms-dos  
DXCap.exe –p regression_test_12.vsglog –toXML temp.xml  
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
