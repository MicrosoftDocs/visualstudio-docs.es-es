---
title: 'Área de prueba 5: Cambiar Control de código fuente | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- source control [Visual Studio SDK], changing
- source control plug-ins, changing source control
ms.assetid: fdf09e00-108c-4d51-bbd5-72452d52a490
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 808ed1ce13af06fa263a339bc9c6788595a261a6
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49229260"
---
# <a name="test-area-5-change-source-control"></a>Área de prueba 5: cambiar control de código fuente
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Esta área de prueba de complemento de control de código fuente trata el cambio del control de código fuente a través de la **cambiar Control de código fuente** comando.  
  
 **Cambiar Control de código fuente** comando proporciona cuatro funciones básicas para el usuario:  
  
-   **Enlazar:**  
  
     Permite al usuario establecer o restablecer un vínculo de control de código fuente entre una solución o proyecto y el almacén de versiones.  
  
-   **Desenlazar:**  
  
     Quita una proyecto o solución de control de código fuente en cada conexión.  
  
-   **Conectar o desconectar acceso:**  
  
 Cambia el estado conectado o desconectado de la solución controlada, que se explica en la zona 3. Para obtener más información, consulte [3 del área de prueba: desproteger o deshacer desprotección](../../extensibility/internals/test-area-3-check-out-undo-checkout.md).  
  
## <a name="command-menu-access"></a>Acceso al menú de comandos  
 La siguiente [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] ruta de acceso del menú de entorno de desarrollo integrado se usa en los casos de prueba.  
  
 Control de código fuente de cambio:**archivo**, **Control de código fuente**, **cambiar Control de código fuente**.  
  
## <a name="test-cases"></a>Casos de prueba  
 Los siguientes son casos de prueba concretos para el **cambiar Control de código fuente** comando área de prueba.  
  
### <a name="case-5a-bind"></a>Caso 5a: enlazar  
 Enlace permite al usuario agregar información de control de código de origen a las soluciones y proyectos seleccionados. Normalmente se solicita el usuario para identificar un proyecto de control de código fuente a la que se trata de agregarse. El usuario no puede crear un nuevo proyecto de control de código fuente como parte de esta operación (oposición a agregar al Control de código fuente).  
  
|Acción|Pasos de prueba|Resultados esperados para comprobar|  
|------------|----------------|--------------------------------|  
|Enlazar a una ubicación vacía|1.  Cree un proyecto.<br />2.  Agregue la solución al control de código fuente.<br />3.  Abra **cambiar Control de código fuente** cuadro de diálogo (**archivo**, **Control de código fuente**, **cambiar Control de código fuente**).<br />4.  Haga clic en **desenlazar**.<br />5.  Si aparece, acepte el cuadro de diálogo de advertencia.<br />6.  Seleccionar todos los elementos.<br />7.  Haga clic en **enlazar**.<br />8.  Vaya a una ubicación vacía en un almacén de control de código fuente.<br />9. Haga clic en **Aceptar** para cerrar el **cambiar Control de código fuente** cuadro de diálogo.<br />10. Haga clic en **continuar con estos enlaces** en el cuadro de diálogo de confirmación.<br />11. Haga clic en **Aceptar** en el cuadro de diálogo de advertencia si aparece.<br />12. Proteger todo. Si este paso se realiza correctamente, vaya al paso siguiente.<br />13. Abrir solución desde el control de código fuente a una nueva ubicación.|`Result from Step 12:`<br /><br /> Soluciones y proyectos están enlazados a y escritos en el destino nuevo en el almacén de versiones.<br /><br /> Se comprueban los archivos de solución y proyecto.<br /><br /> Jerarquía de proyecto del almacén de versión coincide con la jerarquía de carpetas de proyecto en el disco.<br /><br /> `Result from Step 13:`<br /><br /> Se descargan todos los elementos de proyecto.|  
|Enlazar a la ubicación que está sincronizada con el cliente|1.  Cree un proyecto.<br />2.  Agregue la solución al control de código fuente.<br />3.  Crear un duplicado de la solución y proyecto en el almacén de versiones (compartir y bifurcar si usa [!INCLUDE[vsvss](../../includes/vsvss-md.md)]).<br />4.  Abra **cambiar Control de código fuente** cuadro de diálogo (**archivo**, **Control de código fuente**, **cambiar Control de código fuente**).<br />5.  Desenlace todos.<br />6.  Haga clic en **Aceptar** para cerrar **cambiar Control de código fuente** cuadro de diálogo.<br />7.  Vuelva a abrir **cambiar Control de código fuente** cuadro de diálogo.<br />8.  Seleccionar todo.<br />9. Haga clic en **enlazar**.<br />10. Vaya a la ubicación de la solución y proyecto bifurcada (del paso 3)<br />11. Haga clic en **Aceptar** para cerrar el **cambiar Control de código fuente** cuadro de diálogo.<br />12. Obtener todos los elementos más recientes de forma recursiva.|Contenido del archivo después de la operación get es igual que antes de la operación get.|  
|Enlazar a la ubicación que no está sincronizado con el cliente|1.  Cree un proyecto.<br />2.  Agregue la solución al control de código fuente.<br />3.  Crear un duplicado de la solución y proyecto en el almacén de versiones (compartir y bifurcar si usa [!INCLUDE[vsvss](../../includes/vsvss-md.md)]).<br />4.  Modificar los archivos del proyecto en el almacén de versiones bifurcado.<br />5.  Abra **cambiar Control de código fuente** cuadro de diálogo (**archivo**, **Control de código fuente**, **cambiar Control de código fuente**).<br />6.  Desenlace todos.<br />7.  Haga clic en **Aceptar** para cerrar **cambiar Control de código fuente** cuadro de diálogo.<br />8.  Vuelva a abrir **cambiar Control de código fuente** cuadro de diálogo.<br />9. Seleccionar todo.<br />10. Haga clic en **enlazar**.<br />11. Vaya a ramas de ubicación para la solución y proyecto.<br />12. Haga clic en **Aceptar** para cerrar el **cambiar Control de código fuente** cuadro de diálogo.<br />13. Si aparece, acepte el cuadro de diálogo de advertencia.<br />14, Obtener recursiva más reciente para todos los elementos.|También se modifican localmente los archivos que se han modificado en el paso 4.|  
|Enlazar la solución que se encontraba nunca bajo control de código fuente|1.  Cree una carpeta vacía en control de código fuente.<br />2.  Cree un proyecto de cliente.<br />3.  Abra **cambiar Control de código fuente** cuadro de diálogo (**archivo**, **Control de código fuente**, **cambiar Control de código fuente**).<br />4.  Enlazar la solución a una ubicación vacía en control de código fuente.<br />5.  Haga clic en **Aceptar** para cerrar el **cambiar Control de código fuente** cuadro de diálogo.<br />6.  Haga clic en **continuar con estos enlaces** en el cuadro de diálogo de confirmación.<br />7.  Haga clic en **Aceptar** en el cuadro de diálogo de advertencia si aparece.|Solución se agrega al control de código fuente.<br /><br /> Solución y proyecto se desprotegen.|  
|Cancelar el enlace|1.  Cree un proyecto.<br />2.  Agregue la solución al control de código fuente.<br />3.  Abra el cuadro de diálogo Cambiar Control de código fuente.<br />4.  Desenlace todos.<br />5.  Haga clic en **Aceptar** botón para cerrar el cuadro de diálogo. Si este paso se realiza correctamente, vaya al paso siguiente.<br />6.  Vuelva a abrir el **cambiar Control de código fuente** cuadro de diálogo.<br />7.  Enlazar a una ubicación no relacionada.<br />8.  Haga clic en **cancelar**.|`Result from Step 5:`<br /><br /> La solución ya no está bajo control de código fuente<br /><br /> `Result from Step 8:`<br /><br /> Solución está todavía no bajo control de código fuente.|  
  
### <a name="case-5b-unbind"></a>Caso 5b: desenlazar  
 Desenlazar quita información de control de código de origen de sus soluciones y proyectos. La solución y proyectos afectados se basan en una combinación de selección del usuario y cómo se agregaron los elementos de control de código fuente.  
  
|Acción|Pasos de prueba|Resultados esperados para comprobar|  
|------------|----------------|--------------------------------|  
|Desenlazar la solución que contiene un sistema de archivos o un proyecto Web de IIS local y el proyecto de un cliente|1.  Crear un sistema de archivos o un proyecto Web de IIS local.<br />2.  Agregue la solución al control de código fuente.<br />3.  Agregue un nuevo proyecto de cliente a la solución.<br />4.  Si se le solicite, acepte comprobar fuera de la solución.<br />5.  Abra el **cambiar Control de código fuente** cuadro de diálogo.<br />6.  Haga clic en **desenlazar**.<br />7.  Haga clic en **Aceptar** para cerrar el cuadro de diálogo.<br />8.  Intenta desproteger la solución, proyecto, elementos de la solución, los elementos de proyecto.|Soluciones y proyectos no están bajo control de código fuente.<br /><br /> Comandos de menú de Control de código fuente no aparecen.|  
|Desenlazar Cancelar|1.  Cree un proyecto.<br />2.  Agregue la solución al control de código fuente.<br />3.  Abra el **cambiar Control de código fuente** cuadro de diálogo.<br />4.  Haga clic en **desenlazar todos**.<br />5.  Haga clic en **cancelar**.|Solución está bajo control de código fuente.|  
  
### <a name="case-5c-rebind"></a>Caso c de 5: volver a enlazar  
 Volver a vincular es simplemente una combinación de desenlazar y enlazar: el proceso de volver a enlazar una proyecto o solución que estaba bajo control de código fuente y no está enlazado.  
  
|Acción|Pasos de prueba|Resultados esperados para comprobar|  
|------------|----------------|--------------------------------|  
|Volver a enlazar soluciones y proyectos sin cerrar la **cambiar Control de código fuente** cuadro de diálogo|1.  Cree un proyecto.<br />2.  Agregue la solución al control de código fuente.<br />3.  Abra el **cambiar Control de código fuente** cuadro de diálogo.<br />4.  Haga clic en **desenlazar**.<br />5.  Seleccionar todas las filas.<br />6.  Haga clic en **enlazar**.<br />7.  Haga clic en **Aceptar** para cerrar el **cambiar Control de código fuente** cuadro de diálogo.<br />8.  Si se le pida Aceptar la desprotección.|Solución y proyecto están bajo control de código fuente.|  
|Reenlazar proyecto solo sin cerrar **cambiar Control de código fuente** cuadro de diálogo|1.  Cree un proyecto.<br />2.  Agregue solo el proyecto al control de código fuente mediante (archivo -> origen de Control -> Agregar proyectos seleccionados al Control de código fuente.<br />3.  Abra el cuadro de diálogo Cambiar Control de código fuente.<br />4.  Desenlazar solo el proyecto.<br />5.  Enlazar sólo con el proyecto.|Solución permanece no controlada.<br /><br /> Proyecto sigue siendo controlado.|  
|Volver a enlazar la solución solo sin cerrar **cambiar Control de código fuente** cuadro de diálogo|1.  Cree un proyecto.<br />2.  Agregar sólo la solución al control de código fuente mediante (**archivo**, **Control de código fuente**, **agregar proyectos seleccionados al Control de código fuente**.<br />3.  Abra el **cambiar Control de código fuente** cuadro de diálogo.<br />4.  Desenlace solo la solución (no cierre **cambiar Control de código fuente** cuadro de diálogo.)<br />5.  Enlazar sólo con la solución.<br />6.  Haga clic en **Aceptar** para cerrar el cuadro de diálogo.<br />7.  Retirar la solución y elementos de la solución (si la hay)|Solución sigue siendo controlada.<br /><br /> Proyecto sigue siendo no controlado.|  
|Volver a enlazar la solución o proyecto solo cuando en el mismo directorio|1.  Cree un proyecto.<br />2.  Agregue solo el proyecto al control de código fuente mediante (**archivo**, **Control de código fuente**, **agregar proyectos seleccionados al Control de código fuente**.<br />3.  Cierre la solución.<br />4.  Cree una nueva solución con al menos dos proyectos.<br />5.  Agregue la solución al control de código fuente.<br />6.  Agregue el proyecto creado en el paso 1 de control de código fuente.<br />7.  Si se le solicite, acepte la desprotección de la solución.<br />8.  Compruebe en toda la solución.<br />9. Abra el **cambiar Control de código fuente** cuadro de diálogo.<br />10. Seleccione el proyecto agregado (del paso 6) y haga clic en **desenlazar**.<br />11. Haga clic en **Aceptar** para cerrar el cuadro de diálogo.<br />12. Si se le solicite, acepte la desprotección.<br />13. Vuelva a abrir **cambiar Control de código fuente** cuadro de diálogo.<br />14, Seleccione el proyecto agregado (del paso 6) y haga clic en **enlazar**.<br />15. Seleccione la ubicación original.|Soluciones y proyectos siguen siendo controlados.|  
  
## <a name="see-also"></a>Vea también  
 [Guía de pruebas para los complementos de control de código fuente](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)

