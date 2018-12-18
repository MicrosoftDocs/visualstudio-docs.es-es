---
title: Documento de registro de gráficos | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.graphics.vsglog.error
- vs.graphics.experiment
- vs.graphics.vsglog
ms.assetid: 6ccb1269-d55f-49c4-920d-baedf7de2888
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: eab888fa800e8be695b6dca4cf38f2a0ed478ebb
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49931108"
---
# <a name="graphics-log-document"></a>Documento de registro de gráficos
El documento de registro de gráficos es el registro de los eventos de gráficos que se producen mientras se ejecuta la aplicación en una sesión de diagnóstico de gráficos. Cuando el registro se completa, puede examinarlo en el Analizador de gráficos de Visual Studio para diagnosticar problemas de rendimiento y representación.  

 Este es el aspecto de un documento de registro de gráficos en el Analizador de gráficos:  

 ![Un registro de gráficos que contiene dos fotogramas capturados. ](media/gfx_diag_demo_graphics_log_orientation.png "gfx_diag_demo_graphics_log_orientation")  

## <a name="understanding-graphics-log-documents"></a>Comprensión de los documentos de registro de gráficos  
 Si examina un documento de registro de gráficos con el Analizador de gráficos, puede visualizar los efectos de los eventos de Direct3D que se han producido en el destino de presentación durante la captura. Puede aislar regiones del objetivo de presentación que contengan un resultado inesperado. Al seleccionar un píxel de la región afectada, puede utilizar el Diagnóstico de gráficos para inspeccionar el píxel, sus sombreados, los eventos de Direct3D que lo han afectado, la pila de llamadas de la aplicación que ha provocado estos eventos y los objetos de DirectX que los han admitido. Puede utilizar esta información para diagnosticar problemas de presentación de su juego o aplicación.  

 La parte superior de la ventana (**gráfico.vsglog**) muestra la salida de destino actual del fotograma seleccionado y la parte de la parte inferior muestra un **lista de fotogramas** que contiene imágenes en miniatura de la fotogramas capturados.  

#### <a name="to-inspect-a-frame"></a>Para inspeccionar un fotograma  

-   En el **lista de fotogramas**, seleccione el fotograma que desea inspeccionar. El resultado objetivo de presentación de la parte superior del documento de registro de gráficos se actualiza para mostrar el fotograma seleccionado.  

#### <a name="to-inspect-a-pixel"></a>Para inspeccionar un píxel  

-   En la parte superior del documento de registro de gráficos, seleccione el píxel que desee del resultado objetivo de presentación. Cuando se selecciona un píxel, puede usar el **historial de píxeles** ventana para ver información detallada sobre el píxel seleccionado. Para obtener más información, consulte [historial de píxeles](graphics-pixel-history.md).  

## <a name="playback-machine"></a>Máquina de reproducción  
 También se muestra en la esquina superior derecha de la **lista de fotogramas** es el **máquina de reproducción**. La máquina de reproducción es la máquina o dispositivo utilizado para reproducir eventos de gráficos desde un archivo de registro de gráficos durante una sesión de diagnóstico de gráficos posterior. Si utiliza un dispositivo diferente al equipo de desarrollo para reproducir los eventos capturados, puede reproducir de manera más precisa el entorno de ejecución en el que ocurre el problema, por ejemplo, puede utilizar un equipo que tenga un hardware gráfico o unos controladores diferentes de los que utiliza su equipo de desarrollo, u otros tipos de dispositivos, como una tableta Windows basada en ARM o un dispositivo Windows Phone.  

 Para obtener información sobre cómo especificar una máquina de reproducción, consulte [Cómo: cambiar la máquina de reproducción de diagnóstico de gráficos](how-to-change-the-graphics-diagnostics-playback-machine.md).  

## <a name="graphics-log-summary-information"></a>Información de resumen del registro de gráficos  
 Cuando un archivo de registro de gráficos es el documento activo, el **propiedades** ventana muestra información sobre el entorno que hospeda la sesión de captura de diagnóstico de gráficos. Se muestran varias categorías de información.  

 **Información de Direct3D**  
 Enumera información sobre las características del hardware y los controladores del adaptador de pantalla que se ha utilizado durante la sesión de captura.  

|Propiedad|Descripción|  
|--------------|-----------------|  
|**Formato de color de alta densidad XR de 10 bits**|**True** si el formato de color de alta densidad XR de 10 bits es compatible; en caso contrario, **False**.|  
|**DirectCompute CS 4.x**|**True** si Compute Shader 4.0 se admite; en caso contrario, **False**.|  
|**Sombreadores de precisión doble**|**True** si el adaptador de pantalla admite valores de punto flotante de precisión doble (64 bits); en caso contrario, **False**.|  
|**Listas de comandos del controlador**|**True** si el controlador admite listas de comandos; en caso contrario, **False**.|  
|**Creación simultánea de controladores**|**True** si el controlador admite la creación simultánea (asincrónica); en caso contrario, **False**.|  
|**Formatos extendidos (BGRA, etcetera.)**|**True** si formatos extendidos, como BGRA se admiten; de lo contrario, **False**.|  
|**Nivel máximo de HW**|Muestra el nivel de características más elevado que admite el adaptador de pantalla.|  

 **Mostrar información**  
 Enumera la información sobre el adaptador de pantalla que se ha utilizado durante la sesión de captura.  

|Propiedad|Descripción|  
|--------------|-----------------|  
|**Descripción**|La cadena de descripción del adaptador de pantalla.|  
|**Mostrar memoria**|La cantidad de memoria instalada en el adaptador de gráficos.|  
|**Nombre del controlador**|El nombre del controlador del adaptador de gráficos.|  
|**Versión del controlador**|La versión del controlador del adaptador de gráficos.|  
|**Name**|El nombre del adaptador de gráficos.|  

 **Archivo de experimento**  
 Enumera información sobre el archivo de experimento asociado a la sesión de captura.  

|Propiedad|Descripción|  
|--------------|-----------------|  
|**Ruta de acceso**|La ruta del archivo .vsglog. **Nota:** en captura heredada, esta propiedad se utiliza.|  

 **Información de módulo**  
 Enumera el nombre y la versión de las bibliotecas de vínculos dinámicos (DLL) que la aplicación ha cargado durante la sesión de captura.  

 **Información del sistema**  
 Enumera información sobre el hardware y el sistema operativo que ha hospedado la aplicación durante la sesión de captura.  

|Propiedad|Descripción|  
|--------------|-----------------|  
|**Memoria**|La cantidad de memoria instalada en el ordenador.|  
|**Arquitectura del sistema operativo**|La arquitectura de la CPU de destino del sistema operativo.|  
|**Versión del sistema operativo**|La versión del sistema operativo.|  
|**Procesador**|El procesador instalado en el ordenador.|  
|**Arquitectura de la aplicación de destino**|La arquitectura de la CPU de destino de la aplicación. Esto puede ser diferente de la **arquitectura del sistema operativo**.|  

 **Aplicación de destino**  
 Enumera información sobre la aplicación relacionada con la sesión de captura.  

|Propiedad|Descripción|  
|--------------|-----------------|  
|**Fecha y hora de última modificación**|La fecha y hora en la que se creó la aplicación.|  
|**Ruta de acceso**|La ruta de la aplicación.|  
|**Identificador del proceso**|El identificador de proceso que se ha asignado a la aplicación.|  
|**Versión**|La versión de la aplicación.|  

 **Registro Vsg**  
 Enumera información sobre el documento de registro de gráficos.  


| Propiedad | Descripción |
|------------------------| - |
| **Creado por** | El nombre de la aplicación que ha creado el documento de registro de gráficos. Por ejemplo, si la sesión de captura se inició desde [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] (captura manual) el valor de esta propiedad es [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. |
| **Hora de inicio de sesión** | La fecha y hora en la que se inició la sesión de captura. |
| **Size** | El tamaño del documento de registro de gráficos. |

## <a name="see-also"></a>Vea también  
 [Tutorial: Objetos ausentes debido al sombreado de vértices](walkthrough-missing-objects-due-to-vertex-shading.md)   
 [Tutorial: Depurar errores de representación debidos al sombreado](walkthrough-debugging-rendering-errors-due-to-shading.md)