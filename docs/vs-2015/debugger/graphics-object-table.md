---
title: Tabla de objetos gráficos | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.graphics.datavisualizer
- vs.graphics.objecttable
- vs.graphics.bufferviewer
ms.assetid: f48f62d9-16ff-4a2e-8c01-5cbe99513788
caps.latest.revision: 19
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 86279ff4e1721007814163787bd9ed06edc9fb13
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68161168"
---
# <a name="graphics-object-table"></a>Tabla de objetos gráficos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La Tabla de objetos gráficos en el análisis de gráficos de Visual Studio le ayuda a comprender los objetos de Direct3D que admiten un fotograma de su juego o aplicación.  
  
 Esta es la tabla de objetos:  
  
 ![Objetos de Direct3D que se han creado por una aplicación.](../debugger/media/gfx-diag-demo-object-table-orientation.png "gfx_diag_demo_object_table_orientation")  
  
## <a name="understanding-the-graphics-object-table"></a>Descripción de la Tabla de objetos gráficos  
 La Tabla de objetos gráficos permite analizar los objetos de Direct3D que admiten la representación de un fotograma determinado. Puede aislar un problema de representación en un objeto específico examinando sus propiedades y datos (usando otras herramientas de diagnóstico de gráficos anteriormente en el diagnóstico, puede restringir la lista de objetos que podrían no ser los esperados). Cuando encuentre el objeto incorrecto, puede usar una visualización específica de su tipo para examinarlo; por ejemplo, puede usar el Editor de imágenes para ver texturas o el *Visualizador del búfer* para ver el contenido del búfer.  
  
 La Tabla de objetos gráficos admite copiar y pegar, por lo que puede usar otra herramienta (por ejemplo, Microsoft Excel) para examinar su contenido.  
  
### <a name="graphics-object-table-format"></a>Formato de la Tabla de objetos gráficos  
 La Tabla de objetos gráficos muestra los objetos y recursos de Direct3D que admiten el fotograma asociado al evento seleccionado; por ejemplo, objetos de estado, búferes, sombreadores, texturas y otros recursos. Los objetos que se crearon en un fotograma anterior pero que no se usan durante el fotograma capturado se omiten de la tabla de objetos. Los objetos que se han destruido en eventos anteriores durante el fotograma capturado se omiten en los eventos posteriores. Los objetos que no se establecen en D3D10Device o D3D11DeviceContext aparecen como texto en gris. Los objetos se muestran en un formato de tabla.  
  
|Columna|DESCRIPCIÓN|  
|------------|-----------------|  
|**Identificador**|Identificador de objeto.|  
|**Nombre**|Información específica de la aplicación que se ha establecido en el objeto mediante la función `SetPrivateData` de Direct3D (normalmente para proporcionar información de identificación adicional sobre un objeto).|  
|**Type**|Tipo del objeto.|  
|**Active**|Muestra "*" para un objeto que se estableció en D3D10Device o D3D11DeviceContext durante el fotograma capturado.<br /><br /> Esto corresponde a los objetos que se muestran como texto gris, pero proporciona una entrada de columna que se puede utilizar como ayuda para ordenar la tabla de objetos.|  
|**Size**|Tamaño del objeto en bytes.|  
|**Format**|Formato del objeto. Por ejemplo, el formato de un objeto de textura o el modelo de sombreador de un objeto de sombreador.|  
|**Width**|Ancho de un objeto de textura. No se aplica a otros tipos de objeto.|  
|**Height**|Alto de un objeto de textura. No se aplica a otros tipos de objeto.|  
|**Depth**|Profundidad de un objeto de textura en 3D. Si una textura no es 3D, el valor es 0. No se aplica a otros tipos de objeto.|  
|**Mips**|Número de niveles de MIP que tiene un objeto de textura. No se aplica a otros tipos de objeto.|  
|**ArraySize**|Número de texturas en una matriz de textura. El intervalo va de 1 a un límite superior definido por el nivel actual de la característica. Para un mapa de cubo, este valor es 6 veces el número de mapas de cubo de la matriz.|  
|**Muestras**|Número de muestras múltiples por píxel.|  
  
## <a name="graphics-object-viewers"></a>Visores de objetos gráficos  
 Para ver detalles sobre un objeto, ábralo eligiendo su nombre en la tabla de objetos. Los detalles sobre el objeto se muestran en diferentes formatos, según el tipo del objeto. Por ejemplo, las texturas se muestran mediante el Visor de textura y el estado del dispositivo, como el contexto de dispositivo D3D11, se muestra como una lista con formato. Las diferentes versiones de Direct3D usan diferentes objetos, y suele haber visualizadores específicos para los objetos más importantes de cada versión.  
  
 Aquí tenemos el Visor de textura que muestra el contenido de la fase de canalización de fusión de salida.  
  
 ![La versión preliminar de la textura mostrando la fusión de salida](../debugger/media/gfx-diag-texture-preview.png "gfx_diag_texture_preview")  
  
### <a name="d3d12-command-list"></a>Lista de comandos de D3D12  
 En Direct3D 12 una lista de comandos es un objeto que registra comandos en un asignador de comando para que puedan enviarse a la GPU como una única solicitud. Las listas de comandos normalmente realizan una serie de comandos de configuración de estado, dibujo, borrado y copia. Son especialmente importantes porque constituyen el método preferido de representación en Direct3D 12 y se pueden reutilizar entre fotogramas para ayudar a aumentar el rendimiento. Los detalles de la lista de comandos se muestran en una nueva ventana de documento, con información relacionada con cada fase de canalización que se presenta en su propia pestaña.  
  
### <a name="d3d12-pipeline-state-object-pso"></a>Objeto de estado de la canalización (PSO) de D3D12  
 En Direct3D 12 un objeto de estado de la canalización representa una parte significativa del estado de GPU, incluidos todos los sombreadores y ciertos objetos de estado de función fija actualmente establecidos. Una vez creado, un objeto de estado de la canalización es inmutable, una aplicación solo puede cambiar la configuración de la canalización enlazando otro objeto de estado de la canalización. Los detalles del PSO se muestran en una nueva ventana de documento, que pormenoriza la configuración de canalización diseñada jerárquicamente.  
  
### <a name="d3d12-root-signature"></a>Firma raíz de D3D12  
 En Direct3D 12, la firma raíz define todos los recursos que están enlazados a una canalización de gráficos o de cálculo y vincula listas de comandos a los recursos que requieren los sombreadores. Normalmente hay una firma raíz para los gráficos y otra para el cálculo en una aplicación. Los detalles de la firma raíz se muestran en una nueva ventana de documento, que pormenoriza la firma raíz diseñada jerárquicamente.  
  
### <a name="d3d12-resources"></a>Recursos de D3D12  
 En Direct3D 12, los recursos son objetos comodín que proporcionan datos a la canalización de representación; esto difiere de Direct3D11, que define muchos objetos específicos para diferentes tipos y dimensiones de recursos. Un recurso de Direct3D 12 puede contener datos de textura, datos de vértice, datos de sombreador y otros; incluso pueden representar objetivos de representación, como el búfer de profundidad. Los detalles de un recurso de Direct3D 12 se muestran en una nueva ventana de documento; si puede determinar su tipo, el análisis de gráficos usará el visor adecuado para el contenido del objeto de recurso. Por ejemplo, un objeto de recurso que contiene datos de textura se muestra con el Visor de textura, del mismo modo que un objeto Texture2D de D3D11.  
  
### <a name="device-context-object"></a>Objeto de contexto de dispositivo  
 En Direct3D 11 y Direct3D 10, el objeto de contexto de dispositivo (**Contexto de dispositivo D3D11** o **Dispositivo D3D10**) es especialmente relevante porque contiene la información más importante de estado y la vincula a otros objetos de estado establecidos en este momento. Los detalles del contexto de dispositivo se muestran en una nueva ventana de documento y cada categoría de información se muestra allí en su propia pestaña. El contexto de dispositivo cambia cuando se selecciona un nuevo evento para reflejar el estado del dispositivo actual.  
  
### <a name="buffer-object"></a>Objeto de búfer  
 Los detalles del objeto de búfer (Búfer D3D11 o Búfer D3D10) se muestran en una nueva ventana de documento que presenta el contenido del búfer en una tabla y proporciona una interfaz para cambiar cómo se muestra el contenido del búfer. La tabla de **datos del búfer** admite copiar y pegar, por lo que puede utilizar otra herramienta (por ejemplo, Microsoft Excel) para examinar su contenido. El contenido del búfer se interpreta según el valor del cuadro combinado **formato**, que se encuentra sobre la tabla de **datos del búfer**. En el cuadro, puede escribir un formato de datos compuesto que se compone de los tipos de datos que se muestran en la tabla siguiente. Por ejemplo, "float int" muestra una lista de estructuras que contienen un valor de punto flotante de 32 bits seguido de un valor entero de 32 bits con signo. Los formatos de datos compuestos que ha especificado se agregan al cuadro combinado para su uso posterior.  
  
 También puede alternar la casilla **Mostrar desplazamientos** para mostrar u ocultar el desplazamiento de cada elemento en el búfer.  
  
|Type|DESCRIPCIÓN|  
|----------|-----------------|  
|**float**|Valor de punto flotante de 32 bits.|  
|**float2**|Vector que contiene dos valores de punto flotante de 32 bits.|  
|**float3**|Vector que contiene tres valores de punto flotante de 32 bits.|  
|**float4**|Vector que contiene cuatro valores de punto flotante de 32 bits.|  
|**byte**|Valor entero de 8 bits con signo.|  
|**2byte**|Valor entero de 16 bits con signo.|  
|**4byte**|Valor entero de 32 bits con signo. Igual que **int**.|  
|**8byte**|Valor entero de 64 bits con signo. Igual que **int64**.|  
|**xbyte**|Valor hexadecimal de 8 bits.|  
|**x2byte**|Valor hexadecimal de 16 bits.|  
|**x4byte**|Valor hexadecimal de 32 bits. Igual que **xint**.|  
|**x8byte**|Valor hexadecimal de 64 bits. Igual que **xint64**.|  
|**ubyte**|Valor entero de 8 bits sin signo.|  
|**u2byte**|Valor entero de 16 bits sin signo.|  
|**u4byte**|Valor entero de 32 bits sin signo. Igual que **uint**.|  
|**u8byte**|Valor entero de 64 bits sin signo. Igual que **uint64**.|  
|**half**|Valor de punto flotante de 16 bits.|  
|**half2**|Vector que contiene dos valores de punto flotante de 16 bits.|  
|**half3**|Vector que contiene tres valores de punto flotante de 16 bits.|  
|**half4**|Vector que contiene cuatro valores de punto flotante de 16 bits.|  
|**double**|Valor de punto flotante de 64 bits.|  
|**int**|Valor entero de 32 bits con signo. Igual que **4byte**.|  
|**int64**|Valor entero de 64 bits con signo. Igual que **8byte**.|  
|**xint**|Valor hexadecimal de 32 bits. Igual que **x4byte**.|  
|**xint64**|Valor hexadecimal de 64 bits. Igual que **x8byte**.|  
|**uint**|Valor entero de 32 bits sin signo. Igual que **u4byte**.|  
|**uint64**|Valor entero de 64 bits sin signo. Igual que **u8byte**.|  
|**bool**|Valor booleano (`true` o `false`). Cada valor booleano se representa mediante un valor de 32 bits.|  
  
## <a name="see-also"></a>Vea también  
 [Diagnóstico de gráficos (depuración de gráficos DirectX)](../debugger/visual-studio-graphics-diagnostics.md)   
 [Tutorial: Objetos ausentes debido al estado del dispositivo](../debugger/walkthrough-missing-objects-due-to-device-state.md)
