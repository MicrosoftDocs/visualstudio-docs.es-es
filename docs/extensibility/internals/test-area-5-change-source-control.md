---
title: "Zona de ensayo 5: Control de c&#243;digo fuente de cambio | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "control de código fuente [Visual Studio SDK], cambiar"
  - "origen control complementos, Cambiar control de código fuente"
ms.assetid: fdf09e00-108c-4d51-bbd5-72452d52a490
caps.latest.revision: 15
caps.handback.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
---
# Zona de ensayo 5: Control de c&#243;digo fuente de cambio
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Esta área de complemento de prueba de control de código fuente cubre el cambio del control de código fuente a través de la **cambiar Control de código fuente** comando.  
  
 **Cambiar Control de código fuente** comando proporciona cuatro funciones básicas para el usuario:  
  
-   **Enlazar:**  
  
     Permite al usuario establecer o restablecer un vínculo de control de código fuente entre una solución o proyecto y el almacén de versiones.  
  
-   **Desenlace:**  
  
     Quita una proyecto o solución de control de código fuente en cada conexión.  
  
-   **Conectar o desconectar:**  
  
 Cambia el estado conectado o sin conexión de la solución controlada, que se trata en la zona 3. Para obtener más información, consulta [Área de prueba 3: Desproteger o deshacer desprotección](../../extensibility/internals/test-area-3-check-out-undo-checkout.md).  
  
## Acceso al menú de comandos  
 La siguiente [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ruta de acceso del menú de entorno de desarrollo integrado se utiliza en los casos de prueba.  
  
 Cambiar Control de código fuente:**archivo**, **Control de código fuente**, **cambiar Control de código fuente**.  
  
## Casos de prueba  
 Los siguientes son los casos de prueba específicos para la **cambiar Control de código fuente** comando área de prueba.  
  
### Caso 5a: enlazar  
 Enlace permite al usuario agregar información de control de código fuente para las soluciones y proyectos seleccionados. Normalmente se solicita el usuario para identificar un proyecto de control de código fuente a la que se trata de agregarse. El usuario no puede crear un nuevo proyecto de control de código fuente como parte de esta operación \(contraste con agregar al Control de código fuente\).  
  
|Acción|Pasos de prueba|Resultados esperados para comprobar|  
|------------|---------------------|-----------------------------------------|  
|Enlazar a una ubicación vacía|1.  Cree un proyecto.<br />2.  Agregar la solución al control de código fuente.<br />3.  Abra **cambiar Control de código fuente** cuadro de diálogo \(**archivo**, **Control de código fuente**, **cambiar Control de código fuente**\).<br />4.  Haga clic en **Desenlazar**.<br />5.  Acepte el cuadro de diálogo de advertencia si aparece.<br />6.  Seleccionar todos los elementos.<br />7.  Haga clic en **enlazar**.<br />8.  Vaya a una ubicación vacía en un almacén de control de código fuente.<br />9. Haga clic en **Aceptar** para cerrar el **cambiar Control de código fuente** cuadro de diálogo.<br />10. Haga clic en **continuar con estos enlaces** en el cuadro de diálogo de confirmación.<br />11. Haga clic en **Aceptar** en el cuadro de diálogo de advertencia si aparece.<br />12. Proteger todo. Si este paso se realiza correctamente, vaya al paso siguiente.<br />13. Abrir solución desde el control de código fuente a una nueva ubicación.|`Result from Step 12:`<br /><br /> Soluciones y proyectos están enlazados a y escritos en el destino nuevo en el almacén de versiones.<br /><br /> Se registran los archivos de solución y proyecto.<br /><br /> Jerarquía de proyectos de almacén de versión coincide con la jerarquía de carpetas de proyecto en el disco.<br /><br /> `Result from Step 13:`<br /><br /> Se descargan todos los elementos de proyecto.|  
|Enlazar a la ubicación que está sincronizado con el cliente|1.  Cree un proyecto.<br />2.  Agregar la solución al control de código fuente.<br />3.  Crear un duplicado de la solución y el proyecto en el almacén de versiones \(compartir y bifurcar si utiliza [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)]\).<br />4.  Abra **cambiar Control de código fuente** cuadro de diálogo \(**archivo**, **Control de código fuente**, **cambiar Control de código fuente**\).<br />5.  Desenlace todos.<br />6.  Haga clic en **Aceptar** para cerrar **cambiar Control de código fuente** cuadro de diálogo.<br />7.  Vuelva a abrir **cambiar Control de código fuente** cuadro de diálogo.<br />8.  Seleccionar todo.<br />9. Haga clic en **enlazar**.<br />10. Vaya a la ubicación de la solución y proyecto bifurcada \(del paso 3\)<br />11. Haga clic en **Aceptar** para cerrar el **cambiar Control de código fuente** cuadro de diálogo.<br />12. Obtener todos los elementos más recientes de forma recursiva.|Contenido del archivo después de get es igual que antes de obtener.|  
|Enlazar a la ubicación que está sincronizado con el cliente|1.  Cree un proyecto.<br />2.  Agregar la solución al control de código fuente.<br />3.  Crear un duplicado de la solución y el proyecto en el almacén de versiones \(compartir y bifurcar si utiliza [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)]\).<br />4.  Modificar archivos en el proyecto bifurcado en el almacén de versiones.<br />5.  Abra **cambiar Control de código fuente** cuadro de diálogo \(**archivo**, **Control de código fuente**, **cambiar Control de código fuente**\).<br />6.  Desenlace todos.<br />7.  Haga clic en **Aceptar** para cerrar **cambiar Control de código fuente** cuadro de diálogo.<br />8.  Vuelva a abrir **cambiar Control de código fuente** cuadro de diálogo.<br />9. Seleccionar todo.<br />10. Haga clic en **enlazar**.<br />11. Vaya a bifurcado la ubicación de la solución y proyecto.<br />12. Haga clic en **Aceptar** para cerrar el **cambiar Control de código fuente** cuadro de diálogo.<br />13. Acepte el cuadro de diálogo de advertencia si aparece.<br />14. Obtenga más reciente recursiva para todos los elementos.|Archivos que se han modificado en el paso 4 también se modifican localmente.|  
|Solución de enlace que fue nunca bajo control de código fuente|1.  Crear una carpeta vacía en el control de código fuente.<br />2.  Cree un proyecto de cliente.<br />3.  Abra **cambiar Control de código fuente** cuadro de diálogo \(**archivo**, **Control de código fuente**, **cambiar Control de código fuente**\).<br />4.  Enlazar la solución a una ubicación vacía en el control de código fuente.<br />5.  Haga clic en **Aceptar** para cerrar el **cambiar Control de código fuente** cuadro de diálogo.<br />6.  Haga clic en **continuar con estos enlaces** en el cuadro de diálogo de confirmación.<br />7.  Haga clic en **Aceptar** en el cuadro de diálogo de advertencia si aparece.|Solución se agrega al control de código fuente.<br /><br /> Soluciones y proyectos están desprotegidos.|  
|Cancelar el enlace|1.  Cree un proyecto.<br />2.  Agregar la solución al control de código fuente.<br />3.  Abra el cuadro de diálogo Cambiar Control de código fuente.<br />4.  Desenlace todos.<br />5.  Haga clic en **Aceptar** botón para cerrar el cuadro de diálogo. Si este paso se realiza correctamente, vaya al paso siguiente.<br />6.  Vuelva a abrir el **cambiar Control de código fuente** cuadro de diálogo.<br />7.  Enlazar a una ubicación no relacionada.<br />8.  Haga clic en **Cancelar**.|`Result from Step 5:`<br /><br /> La solución ya no está bajo control de código fuente<br /><br /> `Result from Step 8:`<br /><br /> Solución está todavía no bajo control de código fuente.|  
  
### Caso 5b: desenlazar  
 Desenlace quita información de control de código de origen de proyectos y sus soluciones. La solución y los proyectos afectados se basan en una combinación de selección del usuario y cómo se agregaron los elementos de control de código fuente.  
  
|Acción|Pasos de prueba|Resultados esperados para comprobar|  
|------------|---------------------|-----------------------------------------|  
|Desenlace la solución que contiene un sistema de archivos o un proyecto Web de IIS local y proyecto de un cliente|1.  Crear un sistema de archivos o un proyecto Web de IIS local.<br />2.  Agregar la solución al control de código fuente.<br />3.  Agregue un nuevo proyecto de cliente a la solución.<br />4.  Si se le solicita, acepte comprobar fuera de la solución.<br />5.  Abra la **cambiar Control de código fuente** cuadro de diálogo.<br />6.  Haga clic en **Desenlazar**.<br />7.  Haga clic en **Aceptar** para cerrar el cuadro de diálogo.<br />8.  Intenta desproteger soluciones, proyectos, elementos de la solución, elementos de proyecto.|Soluciones y proyectos no están bajo control de código fuente.<br /><br /> Comandos de menú de Control de código fuente no aparecen.|  
|Cancelar desenlace|1.  Cree un proyecto.<br />2.  Agregar la solución al control de código fuente.<br />3.  Abra la **cambiar Control de código fuente** cuadro de diálogo.<br />4.  Haga clic en **desenlazar todos**.<br />5.  Haga clic en **Cancelar**.|Solución está bajo control de código fuente.|  
  
### Caso 5c: reenlazar  
 Reenlace es simplemente una combinación de separación y el enlace, el proceso de reenlace de una proyecto o solución que anteriormente estaba bajo control de código fuente y era independiente.  
  
|Acción|Pasos de prueba|Resultados esperados para comprobar|  
|------------|---------------------|-----------------------------------------|  
|Volver a enlazar soluciones y proyectos sin cerrar la **cambiar Control de código fuente** cuadro de diálogo|1.  Cree un proyecto.<br />2.  Agregar la solución al control de código fuente.<br />3.  Abra la **cambiar Control de código fuente** cuadro de diálogo.<br />4.  Haga clic en **Desenlazar**.<br />5.  Seleccionar todas las filas.<br />6.  Haga clic en **enlazar**.<br />7.  Haga clic en **Aceptar** para cerrar el **cambiar Control de código fuente** cuadro de diálogo.<br />8.  Aceptar la desprotección si se le solicita.|Solución y proyecto están bajo control de código fuente.|  
|Vuelva a enlazar el proyecto sólo sin cerrar **cambiar Control de código fuente** cuadro de diálogo|1.  Cree un proyecto.<br />2.  Agregar sólo el proyecto al control de código fuente mediante \(archivo \-\> origen de Control \-\> Agregar proyectos seleccionados al Control de código fuente.<br />3.  Abra el cuadro de diálogo Cambiar Control de código fuente.<br />4.  Desenlace sólo en el proyecto.<br />5.  Enlazar sólo en el proyecto.|Solución permanece no controlada.<br /><br /> Proyecto permanece controlado.|  
|Volver a enlazar soluciones sólo sin cerrar **cambiar Control de código fuente** cuadro de diálogo|1.  Cree un proyecto.<br />2.  Agregar sólo la solución al control de código fuente mediante \(**archivo**, **Control de código fuente**, **Agregar proyectos seleccionados al Control de código fuente**.<br />3.  Abra la **cambiar Control de código fuente** cuadro de diálogo.<br />4.  Desenlace sólo la solución \(no cierre **cambiar Control de código fuente** cuadro de diálogo.\)<br />5.  Enlazar sólo con la solución.<br />6.  Haga clic en **Aceptar** para cerrar el cuadro de diálogo.<br />7.  Retirar la solución y elementos de la solución \(si la hay\)|Solución permanece controlada.<br /><br /> Proyecto permanece no controlado.|  
|Volver a enlazar la solución o proyecto sólo cuando en el mismo directorio|1.  Cree un proyecto.<br />2.  Agregar sólo el proyecto al control de código fuente mediante \(**archivo**, **Control de código fuente**, **Agregar proyectos seleccionados al Control de código fuente**.<br />3.  Cierre la solución.<br />4.  Crear una nueva solución con al menos dos proyectos.<br />5.  Agregar la solución al control de código fuente.<br />6.  Agregue el proyecto creado en el paso 1 de control de código fuente.<br />7.  Si se le solicita, acepte la desprotección de la solución.<br />8.  Compruebe en toda la solución.<br />9. Abra la **cambiar Control de código fuente** cuadro de diálogo.<br />10. Seleccione el proyecto agregado \(del paso 6\) y haga clic en **Unbind**.<br />11. Haga clic en **Aceptar** para cerrar el cuadro de diálogo.<br />12. Si se le solicita, acepte la desprotección.<br />13. Vuelva a abrir **cambiar Control de código fuente** cuadro de diálogo.<br />14. Seleccione el proyecto agregado \(del paso 6\) y haga clic en **enlazar**.<br />15. Seleccione la ubicación original.|Soluciones y proyectos permanecen controlados.|  
  
## Vea también  
 [Guía de pruebas para los complementos de Control de código fuente](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)