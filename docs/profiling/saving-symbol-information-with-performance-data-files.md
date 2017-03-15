---
title: "Guardar información de símbolos con archivos de datos de rendimiento | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- packsymbols, in profiling tools reports
- profiling tools, packsymbols
ms.assetid: 8b802505-e94d-4ee0-83e4-fdd790a332c1
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 6193453b9cbdaab387c6fff9e883d43dc436c41b
ms.lasthandoff: 02/22/2017

---
# <a name="saving-symbol-information-with-performance-data-files"></a>Guardar información de símbolos con archivos de datos de rendimiento
Si está utilizando el entorno de desarrollo integrado (IDE) de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] para analizar los archivos y planea mover el archivo VSP a otro equipo, debe establecer la configuración del proyecto de rendimiento para guardar o *serializar* símbolos en el archivo de informe. Esto aumenta el tamaño de un archivo de informe. Es necesario serializar símbolos por dos motivos:  
  
-   Para incrustar símbolos de código en un informe de rendimiento antes de que se pierdan los ensamblados de destino de su ubicación en el almacenamiento temporal.  
  
-   Para conservar los símbolos para que se pueda mover el informe de rendimiento desde el equipo del que se generan perfiles y que genere la misma información si se abre el informe para analizarlo en otro equipo, que podría tener símbolos diferentes.  
  
 **Requisitos**  
  
-   [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)], [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]  
  
 Puede serializar símbolos desde el IDE de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] o desde la línea de comandos:  
  
-   Para serializar símbolos en el IDE de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], seleccione **Herramientas** en la barra de menús y después haga clic en **Opciones**. En la ventana **Opciones**, seleccione **Herramientas de rendimiento** y después la casilla **Serializar automáticamente información de símbolos**.  
  
-   PACKSYMBOLS es la opción de línea de comandos equivalente al guardar los archivos de informe. Para serializar símbolos, escriba **vsperfreport /summary:all /packsymbols filename.vsp**.  
  
## <a name="troubleshooting-symbol-problems"></a>Solución de problemas de símbolos  
 Si no ve todos los símbolos en su propio código, existen algunas soluciones comunes:  
  
-   Ejecute vsperfreport /debugsympath en una línea de comandos para mostrar una lista completa de las ubicaciones donde los componentes del generador de perfiles están cargando información de símbolos y si coinciden los archivos de símbolos que se utilizan con los archivos que utiliza el proyecto.  
  
-   Asegúrese de que ejecuta vsperfreport con la marca /PACKSYMBOLS o, en el IDE de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], que tiene seleccionada la opción de serializar información de símbolos en las opciones del explorador de rendimiento general.  
  
-   Si recopiló datos de tipos, agregue /SUMMARY:TYPE a la línea de comandos de vsperfreport.  
  
 Si no ve los símbolos de Windows u otros programas de Microsoft:  
  
-   Asegúrese de que ha establecido la ruta de acceso de la memoria caché de símbolos de Windows. Realice una de las siguientes acciones para establecer la ruta de acceso a la memoria caché de símbolos:  
  
    -   Establezca la opción Depurador->Símbolos en el IDE de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] para la ruta de acceso correcta.  
  
    -   Agregue la opción -symbolpath a la línea de comandos de VSPerfReport para incluir sus símbolos.  
  
-   Si no ve los símbolos en [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)], asegúrese de que el servidor de símbolos está configurado correctamente para el servidor ASP.  
  
## <a name="repacking-symbols"></a>Volver a empaquetar símbolos  
 Si desea volver a empaquetar los símbolos en un informe, puede hacerlo mediante la herramienta de línea de comandos VsPerfReport. Use las siguientes líneas de comando:  
  
 VsPerfReport -clearpackedsymbols filename.vsp  
  
 VsPerfReport -packsymbols -summary:all filename.vsp  
  
## <a name="see-also"></a>Vea también  
 [Guardar y exportar datos de herramientas de rendimiento](../profiling/saving-and-exporting-performance-tools-data.md)   
 [Cómo: Hacer referencia a información de símbolos de Windows](../profiling/how-to-reference-windows-symbol-information.md)   
 [VSPerfReport](../profiling/vsperfreport.md)
