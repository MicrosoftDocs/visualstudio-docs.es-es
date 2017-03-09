---
title: "C&#243;mo funciona Diagn&#243;stico de gr&#225;ficos | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2ae14497-c77c-4399-bc0c-595caba23656
caps.latest.revision: 2
caps.handback.revision: 2
ms.author: "mithom"
manager: "douge"
---
# C&#243;mo funciona Diagn&#243;stico de gr&#225;ficos
Inserte aquí la introducción.  
  
## Cómo funciona Diagnóstico de gráficos  
 Para usar Diagnóstico de gráficos, primero debe registrar información sobre cómo una aplicación utiliza la API de Direct3D mientras se ejecuta y después examinar el comportamiento registrado.  Para los fotogramas especificados, la información que se registra incluye llamadas API \(como las que borran la pantalla, dibujan la geometría, envían sombreadores de cálculo o cambian el estado del dispositivo gráfico\), además de sus argumentos y las copias de búferes y objetos a los que se hace referencia indirectamente.  Asimismo, las llamadas API relacionadas con la configuración y la inicialización se registran ante de que se representen los fotogramas.  La información que se registra se escribe en un archivo de *registro de gráficos* \(.vsglog\).  
  
 Deberá recrear el comportamiento de representación recopilado en el registro de gráficos reproduciendo los eventos de gráficos en el equipo de desarrollo o en un equipo o dispositivo remoto.  El equipo de reproducción puede ser el mismo equipo o dispositivo donde se recopiló el registro de gráficos o uno diferente.  Para la mayoría de las características de reproducción, se utiliza el hardware gráfico del equipo de reproducción para reproducir eventos de gráficos, pero cuando se usa el depurador de HLSL, el código del sombreador siempre se reproduce mediante una GPU emulada en la CPU.  El uso de una GPU emulada permite recorrer el código del sombreador, inspeccionar variables y usar otras características de depuración comunes independientemente de si el hardware gráfico del equipo de reproducción admite la depuración de hardware.  
  
> [!NOTE]
>  Aunque un registro de gráficos captura la mayoría de la información pertinente internamente, se requiere información adicional para usar plenamente algunas de las características de Diagnóstico de gráficos.  Por ejemplo, para usar la característica de pila de llamadas de gráficos en su totalidad, también tiene que tener el archivo de base de datos del programa \(.pdb\) y el código fuente de la aplicación.  Para depurar código fuente del sombreador de HLSL, también tiene que tener el código fuente del sombreador.  \(Si el sombreador se compila con el compilador del sombreador D3D11.1 y se habilita la información de depuración, el código fuente del sombreador se inserta en el registro de gráficos durante la captura\).  
  
> [!NOTE]
>  Como algunas API pueden no estar disponibles en versiones anteriores de Windows o DirectX, no puede reproducir registros de gráficos que han capturado estas llamadas API en una máquina de reproducción que no los admite.  
  
### Registros de gráficos  
 Un registro de gráficos contiene uno o varios fotogramas capturados desde una aplicación de gráficos DirectX en ejecución.  Como los registros de gráficos son independientes entre sí, estos fotogramas se pueden volver a crear más tarde sin información o referencias externas.  Esto significa que puede compartir los registros de gráficos con otros desarrolladores, examinar problemas en equipos diferentes y examinar antiguos registros de gráficos incluso si los modelos y las texturas se han cambiado en el desarrollo.  También puede cargar varios archivos de registro de gráficos \(.vsglog\) al mismo tiempo para comparar los datos y los resultados de representación.  
  
##### Para abrir un archivo de registro de gráficos \(vsglog\)  
  
1.  En [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], en la barra de menús, elija **Archivo**, **Abrir**, **Archivo**.  Aparece el cuadro de diálogo **Abrir archivo**.  
  
2.  Especifique un archivo de registro de gráficos \(.vsglog\) para abrirlo y, a continuación, elija el botón **Abrir**.  
  
> [!NOTE]
>  Puede extraer, modificar y guardar copias de mallas y texturas de un registro de gráficos mediante las herramientas de gráficos que forman parte de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  Sin embargo, el contenido del registro de gráficos no se ve afectado por estas modificaciones.  Para obtener información sobre estas herramientas de gráficos, consulte [Trabajar con activos 3D para juegos y aplicaciones](../designers/working-with-3-d-assets-for-games-and-apps.md).