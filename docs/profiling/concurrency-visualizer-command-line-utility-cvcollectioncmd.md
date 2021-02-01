---
title: Utilidad de línea de comandos del Visualizador de simultaneidad
description: Use la utilidad de línea de comandos de CVCollectionCmd.exe para recopilar seguimientos que puede ver en el visualizador de simultaneidad. No necesita tener Visual Studio instalado.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.performance.cvcollectioncmd
ms.assetid: 476601be-1608-4014-af15-5aba6ccbed1c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6970c582b6f3ac254f5bbb60f0324128dac63cfe
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2021
ms.locfileid: "98721052"
---
# <a name="concurrency-visualizer-command-line-utility-cvcollectioncmd"></a>Utilidad de la línea de comandos del visualizador de simultaneidad (CVCollectionCmd)
Se puede usar la utilidad de la línea de comandos (*CVCollectionCmd.exe*) del Visualizador de simultaneidad para recopilar seguimientos desde la línea de comandos de manera que los pueda ver en el Visualizador de simultaneidad para Visual Studio. Las herramientas se pueden usar en equipos que no tengan instalado Visual Studio.

> [!NOTE]
> Desde Visual Studio 2013, el Visualizador de simultaneidad es una extensión opcional. (Anteriormente se incluía en Visual Studio.) Puede descargar las [Herramientas de recolección del visualizador de simultaneidad para Visual Studio 2015](https://www.microsoft.com/download/details.aspx?id=49103) desde el Centro de descarga.

## <a name="download-the-concurrency-visualizer-command-line-utility"></a>Descarga de la utilidad de línea de comandos del Visualizador de simultaneidad
 Para descargar e instalar la utilidad de línea de comandos, vaya a [Herramientas de recolección del visualizador de simultaneidad para Visual Studio 2015](https://www.microsoft.com/download/details.aspx?id=49103) y siga las instrucciones. De forma predeterminada, *CVCollectionCmd.exe* se instala en %ProgramFiles%\Microsoft Concurrency Visualizer Collection Tools\ (%ProgramFiles(x86)%\Microsoft Concurrency Visualizer Collection Tools\ en equipos x64).

## <a name="collect-a-trace-with-cvcollectioncmd"></a>Recopile datos de un seguimiento con CVCollectionCmd
 Para recopilar información de un seguimiento, inicie la aplicación con CVCollectionCmd o asóciela a ella. Consulte la siguiente referencia de comandos para conocer las opciones disponibles. Por ejemplo

```cmd
<Path>CVCollectionCmd /launch c:\myapp\myapp.exe /outdir c:\myapp\data
```

## <a name="commands-and-parameters"></a>Comandos y parámetros
 Para obtener ayuda sobre los comandos y parámetros de la utilidad de la línea de comandos, escriba esto en el símbolo del sistema:

 **CvCollectionCmd /?**

|Opción|Descripción|Parámetros|Valores devueltos|
|------------|-----------------|----------------|-------------------|
|Consulta|Devuelve si la recolección se puede iniciar.|None|0 si la recolección está lista para comenzar.<br /><br /> 1 si la recolección ya está en curso.<br /><br /> 2 si la recolección no está en curso, pero una o más de las sesiones de [ETW](/dotnet/framework/wcf/samples/etw-tracing) necesarias ya están habilitadas.|
|Launch|Ejecuta el proceso especificado en el Visualizador de simultaneidad.|Ruta de acceso del archivo ejecutable.|0 si la ejecución se realizó correctamente.<br /><br /> 1 si se ha producido un error en la ejecución porque no se pudo iniciar la aplicación de destino.<br /><br /> 13 si se produjo un error en la ejecución porque CVCollectionCmd no tenía permisos suficientes para escribir en el directorio de salida especificado.|
|Attach|Comienza a recopilar un seguimiento de todo el sistema; de lo contrario, se asocia a un proceso si se ha especificado uno.|Ninguno.|0 si la asociación se realizó correctamente.<br /><br /> 1 si se produjo un error en la asociación porque el proceso especificado no era válido o era ambiguo.<br /><br /> 13 si se produjo un error en la asociación porque CVCollectionCmd no tenía permisos suficientes para escribir en el directorio de salida especificado.|
|Desasociar|Detiene la recolección.|Ninguno.|0 si la desasociación se realizó correctamente.<br /><br /> 1 si se produjo un error en la desasociación porque la recolección no estaba actualmente en curso.<br /><br /> 2 si se produjo un error en la desasociación porque no se pudo detener la recolección.|
|Analizar|Analiza el seguimiento especificado.|Ruta de acceso completa del archivo CVTrace.|0 si el análisis se realizó correctamente.<br /><br /> 1 si el análisis no puede comenzar porque el seguimiento especificado abarca todo el sistema, pero no se especificó ningún proceso de destino.<br /><br /> 2 si el análisis no puede comenzar porque el seguimiento no abarcaba todo el sistema y se especificó un proceso.<br /><br /> 3 si se produjo un error en el análisis porque el proceso especificado no es válido.<br /><br /> 4 si se produjo un error en el análisis porque el archivo CVTrace especificado no es válido.|
|LaunchArgs|Especifica los argumentos del archivo ejecutable de destino. Esta opción es aplicable solo al comando Launch.|Argumentos de la línea de comandos para la aplicación.|Ninguno.|
|Outdir|Especifica el directorio en el que se guardarán los archivos de seguimiento. Se aplica a los comandos Launch y Attach.|Ruta de acceso del directorio o relativa.|Ninguno.|
|Proceso|Especifica el proceso al que asociar cuando se ejecuta el comando Attach o el proceso en un seguimiento que analizar cuando se ejecuta el comando Analyze. Se aplica a los comandos Attach y Analyze.|PID o nombre del proceso.|Ninguno.|
|Configuración|Especifica la ruta de acceso del archivo de configuración si quiere que la configuración de la recolección sea distinta de la predeterminada.   Se aplica a los comandos Launch, Attach y Analyze.|Ruta de acceso del directorio o relativa del archivo de configuración XML.|Ninguno.|

## <a name="customize-configuration-settings"></a>Personalizar las opciones de configuración
 Si utiliza CVCollectionCmd para recopilar seguimientos y desea personalizar las opciones de configuración, use un archivo de configuración para especificarlos.

> [!NOTE]
> Si utiliza Visual Studio para recopilar seguimientos, no modifique directamente el archivo de configuración.  En su lugar, use el cuadro de diálogo [Configuración avanzada](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) para modificar la configuración.

 Para modificar la configuración de la recolección, cree un archivo de configuración en la máquina donde se ejecutará la utilidad CVCollectionCmd. Puede crear el archivo de configuración desde cero o copiar el archivo de configuración en el equipo que tiene Visual Studio instalado y modificarlo. El archivo se denomina *UserConfig.xml* y se encuentra en la carpeta *Local AppData*. Cuando ejecute la utilidad, use la opción Config con el comando Launch, Attach o Analyze.  En el parámetro asociado a la opción Config, especifique la ruta de acceso del archivo de configuración.

### <a name="configuration-file-tags"></a>Etiquetas del archivo de configuración
 El archivo de configuración está basado en XML. A continuación se muestran las etiquetas y los valores válidos:

| Etiqueta | Descripción | Valores |
|-------------------------| - | - |
| Configuración | Delimita el archivo de configuración global. | Debe contener estos elementos:<br /><br /> -   MinorVersion<br />-   MajorVersion |
| MajorVersion | Especifica la versión principal del archivo de configuración. | Debe ser 1 para los proyectos de [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] . Si no es 1, la utilidad no funcionará. |
| MinorVersion | Especifica la versión secundaria del archivo de configuración. | Debe ser 0 para los proyectos de [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] . Si no es 0, la utilidad no funcionará. |
| IncludeEnvSymbolPath | Establece un valor que determina si se usa la ruta de acceso de símbolo de entorno (_NT_SYMBOL_PATH). | -   True<br />-   False |
| DeleteEtlsAfterAnalysis | Establece un valor que determina si se eliminan los archivos ETL cuando se completa el análisis. | -   True<br />-   False |
| SymbolPath | Especifica la ruta de acceso del servidor de símbolos. Para más información, vea [Utilizar el servidor de símbolos de Microsoft para obtener archivos de símbolos de depuración](/windows/win32/dxtecharts/debugging-with-symbols). | Nombre de directorio o dirección URL. |
| Markers | Contiene la lista de proveedores de marcadores. | Puede contener cero o más elementos MarkerProvider. |
| MarkerProvider | Especifica un proveedor de marcadores único. | Debe contener estos elementos:<br /><br /> -   Level<br />-   GUID<br />-   Name<br /><br /> Puede contener estos elementos:<br /><br /> -   Categories<br />-   IsEnabled |
| Nivel | Establece el nivel de importancia de un MarkerProvider. | -   Low<br />-   Normal<br />-   High<br />-   Critical<br />-   Everything |
| GUID | Identificador único global del proveedor de marcadores ETW. | Un GUID. |
| NOMBRE | Especifica la descripción del proveedor de marcadores. | Una cadena. |
| Categorías | Especifica las categorías recopiladas por el proveedor de marcadores. | Cadena delimitada por comas de números o intervalos de números. |
| IsEnabled | Establece un valor que determina si el proveedor de marcadores está habilitado para la recolección. | -   True<br />-   False |
| FilterConfig | Especifica la lista de opciones de configuración de los eventos ETW que se filtran de la recolección. | Puede contener estos elementos:<br /><br /> -   CollectClrEvents<br />-   ClrCollectionOptions<br />-   CollectSampleEvents<br />-   CollectGpuEvents<br />-   CollectFileIO |
| CollectClrEvents | Establece un valor que determina si se recopilan eventos CLR. | -   True<br />-   False |
| ClrCollectionOptions | Especifica si se recopilan eventos CLR para aplicaciones nativas y si se van a recopilar eventos de detención de NGEN. | Puede contener uno, ambos o ninguno de estos valores:<br /><br /> -   CollectForNative<br />-   DisableNGenRundown |
| CollectSampleEvents | Establece un valor que determina si se recopilan eventos de muestreo. | -   True<br />-   False |
| CollectGpuEvents | Establece un valor que determina si se recopilan los eventos que genere DX. | -   True<br />-   False |
| CollectFileIO | Establece un valor que determina si se recopilan eventos de E/S de archivo. | -   True<br />-   False |
| UserBufferSettings | Especifica la lista de parámetros de configuración de búfer del usuario. | Debe contener estos elementos:<br /><br /> -   BufferFlushTimer<br />-   BufferSize<br />-   MinimumBuffers<br />-   MaximumBuffers |
| KernelBufferSettings | Especifica la lista de parámetros de configuración de búfer del kernel. | Debe contener estos elementos:<br /><br /> -   BufferFlushTimer<br />-   BufferSize<br />-   MinimumBuffers<br />-   MaximumBuffers |
| BufferFlushTimer | Especifica el temporizador de vaciado de los búferes ETW. | Un entero positivo. |
| BufferSize | Cantidad de memoria asignada para cada búfer de sesión de seguimiento de eventos, en kilobytes. | Un número del 0 al 1.024. |
| MinimumBuffers | Número mínimo de búferes asignados para el grupo de búferes de la sesión de seguimiento de eventos. | Un entero positivo mayor o igual que el doble del número de núcleos lógicos. |
| MaximumBuffers | Número máximo de búferes asignados para el grupo de búferes de la sesión de seguimiento de eventos. | Un número mayor o igual que el valor de MinimumBuffers. |
| JustMyCode | Especifica la lista de directorios de Solo mi código. | Una lista de cero o más elementos MyCodeDirectory. |
| MyCodeDirectory | Especifica un directorio que contiene el código. | Una ruta de acceso absoluta. |

### <a name="example"></a>Ejemplo
 En lugar de crear un archivo de configuración desde el principio, puede copiar el ejemplo siguiente y después modificarlo para que se ajuste a sus necesidades.

```xml
<?xml version="1.0"?>
<LocalConfig xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" MajorVersion="1" MinorVersion="0">

  <IncludeEnvSymbolPath>true</IncludeEnvSymbolPath>

  <DeleteEtlsAfterAnalysis>true</DeleteEtlsAfterAnalysis>

  <TraceLocation>C:\traces</TraceLocation>

  <SymbolPath>http://symweb</SymbolPath>

  <Markers>
    <MarkerProvider Name="Default" Guid="8d4925ab-505a-483b-a7e0-6f824a07a6f0" Level="Low" />
    <MarkerProvider Name="TPL" Guid="2e5dba47-a3d2-4d16-8ee0-6671ffdcd7b5" Level="Normal" />
    <MarkerProvider Name="TPL Dataflow" Guid="16f53577-e41d-43d4-b47e-c17025bf4025" Level="Normal" />
    <MarkerProvider Name="TPL Synchronization" Guid="ec631d38-466b-4290-9306-834971ba0217" Level="Normal" />
    <MarkerProvider Name="PLINQ" Guid="159eeeec-4a14-4418-a8fe-faabcd987887" Level="Normal" />
    <MarkerProvider Name="Concurrency Runtime" Guid="f7b697a3-4db5-4d3b-be71-c4d284e6592f" Level="Normal" />
    <MarkerProvider Name="Scenario Markers" Guid="fb9244c9-f23a-4966-8a9c-97a51f8c355b" Level="Low" />

    <!-- The IsEnabled and Categories elements are optional -->
    <MarkerProvider Name="myMarker1" Guid="d0dbb3a3-895c-4ce6-96d9-28f69d664dc3" Level="Critical" IsEnabled="false" Categories="0,1,3-5,8" />
    <MarkerProvider Name="myMarker2" Guid="03452127-a617-4302-9e30-c0d10442e4ee" Level="Low" IsEnabled="false" Categories="0,1,3-5,8-10,11-13" />
  </Markers>

  <FilterConfig>
    <CollectClrEvents>true</CollectClrEvents>
    <ClrCollectionOptions>CollectForNative DisableNGenRundown</ClrCollectionOptions>
    <CollectSampleEvents>true</CollectSampleEvents>
    <CollectGpuEvents>true</CollectGpuEvents>
    <CollectFileIO>true</CollectFileIO>
  </FilterConfig>

  <UserBufferSettings>
    <BufferFlushTimer>0</BufferFlushTimer>
    <BufferSize>256</BufferSize>
    <MinimumBuffers>512</MinimumBuffers>
    <MaximumBuffers>1024</MaximumBuffers>
  </UserBufferSettings>

  <KernelBufferSettings>
    <BufferFlushTimer>0</BufferFlushTimer>
    <BufferSize>256</BufferSize>
    <MinimumBuffers>512</MinimumBuffers>
    <MaximumBuffers>1024</MaximumBuffers>
  </KernelBufferSettings>

  <!-- List of MyCodeDirectory directories -->
  <JustMyCode>
    <MyCodeDirectory>C:\myBinaries1</MyCodeDirectory>
    <MyCodeDirectory>C:\myBinaries2</MyCodeDirectory>
  </JustMyCode>
</LocalConfig>

```
