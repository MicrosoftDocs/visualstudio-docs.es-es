---
title: 'Zona de prueba 5: Cambiar el control de código fuente ( Source Control ) Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], changing
- source control plug-ins, changing source control
ms.assetid: fdf09e00-108c-4d51-bbd5-72452d52a490
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d1c0df31fbecd532e6a5f7f317730cd995cd8225
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704528"
---
# <a name="test-area-5-change-source-control"></a>Área de prueba 5: cambiar control de código fuente
Este área de prueba del complemento de control de código fuente cubre el cambio del control de código fuente mediante el comando **Cambiar control de código fuente.**

 **El** comando Change Source Control proporciona cuatro funciones básicas para el usuario:

- **Atar:**

   Permite a un usuario establecer o restablecer un vínculo de control de código fuente entre una solución o proyecto y el almacén de versiones.

- **Desvincular:**

   Quita un proyecto o solución del control de código fuente por conexión.

- **Conectar/Desconectar:**

  Alterna el estado conectado o sin conexión de la solución controlada, que se cubre en el área 3. Para obtener más información, consulte Zona de [prueba 3: Desproteger/Deshacer desprotección](../../extensibility/internals/test-area-3-check-out-undo-checkout.md).

## <a name="command-menu-access"></a>Acceso al menú de comandos
 La [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] siguiente ruta de menú del entorno de desarrollo integrado se utiliza en los casos de prueba.

 Cambiar control de código fuente:**Archivo**, **Control de código fuente**, Cambiar control de código **fuente**.

## <a name="test-cases"></a>Casos de prueba
 A continuación se muestran casos de prueba específicos para el área de prueba del comando **Cambiar control de código fuente.**

### <a name="case-5a-bind"></a>Caso 5a: Enlazar
 Enlazar permite al usuario agregar información de control de código fuente a los proyectos y soluciones seleccionados. Normalmente se solicita al usuario que identifique un proyecto en el control de código fuente al que se van a agregar. El usuario no puede crear un nuevo proyecto en el control de código fuente como parte de esta operación (contraste con Agregar al control de código fuente).

| Acción | Pasos de prueba | Resultados esperados para verificar |
| - | - | - |
| Enlazar a una ubicación vacía | 1. Cree un proyecto.<br />2. Agregue la solución al control de código fuente.<br />3. Abra el cuadro de diálogo **Cambiar control de código fuente** (**Archivo**, Control de **código fuente**, Cambiar control de **código fuente**).<br />4. Haga clic en **Desvincular**.<br />5. Acepte el cuadro de diálogo de advertencia si aparece.<br />6. Seleccione todos los elementos.<br />7. Haga clic en **Enlazar**.<br />8. Vaya a una ubicación vacía en un almacén de control de código fuente.<br />9. Hacer clic **OK** para cerrar el cuadro de diálogo **Cambiar control de código fuente.**<br />10. Haga clic en **Continuar con estos enlaces** en el cuadro de diálogo de confirmación.<br />11. Haga clic en **Aceptar** en el cuadro de diálogo de advertencia si aparece.<br />12. Compruebe todo. Si este paso se realiza correctamente, continúe con el paso siguiente.<br />13. Abra la solución desde el control de código fuente a una nueva ubicación. | `Result from Step 12:`<br /><br /> La solución y el proyecto se enlazan y escriben en el nuevo destino en el almacén de versiones.<br /><br /> Los archivos de solución y proyecto están protegidos.<br /><br /> La jerarquía del proyecto de almacén de versiones coincide con la jerarquía de carpetas del proyecto en disco.<br /><br /> `Result from Step 13:`<br /><br /> Se descargan todos los elementos del proyecto. |
| Enlazar a la ubicación que está sincronizada con el cliente | 1. Cree un proyecto.<br />2. Agregue la solución al control de código fuente.<br />3. Cree un duplicado de la solución y el [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)]proyecto en el almacén de versiones (Compartir y rama si usa ).<br />4. Abra el cuadro de diálogo **Cambiar control de código fuente** (**Archivo**, Control de **código fuente**, Cambiar control de **código fuente**).<br />5. Desenlazar todo.<br />6. Hacer clic **OK** para cerrar **Cambiar control de código fuente** cuadro de diálogo.<br />7. Vuelva a abrir el cuadro de diálogo **Cambiar control de código fuente.**<br />8. Seleccione todo.<br />9. Haga clic en **Enlazar**.<br />10. Vaya a la ubicación ramificada de la solución y el proyecto (del paso 3)<br />11. Hacer clic **OK** para cerrar el cuadro de diálogo **Cambiar control de código fuente.**<br />12. Obtenga la última recursiva para todos los artículos. | El contenido del archivo después de la obtención es el mismo que antes de la obtención. |
| Enlazar a una ubicación que no está sincronizada con el cliente | 1. Cree un proyecto.<br />2. Agregue la solución al control de código fuente.<br />3. Cree un duplicado de la solución y el [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)]proyecto en el almacén de versiones (Compartir y rama si usa ).<br />4. Modifique los archivos del proyecto ramificado en el almacén de versiones.<br />5. Abra el cuadro de diálogo **Cambiar control de código fuente** (**Archivo**, Control de **código fuente**, Cambiar control de **código fuente**).<br />6. Desenlazar todo.<br />7. Hacer clic **OK** para cerrar **Cambiar control de código fuente** cuadro de diálogo.<br />8. Vuelva a abrir el cuadro de diálogo **Cambiar control de código fuente.**<br />9. Seleccione todo.<br />10. Haga clic en **Enlazar**.<br />11. Vaya a la ubicación ramificada para la solución y el proyecto.<br />12. Hacer clic **OK** para cerrar el cuadro de diálogo **Cambiar control de código fuente.**<br />13. Acepte el cuadro de diálogo Advertencia si aparece.<br />14. Obtener la última recursiva para todos los elementos. | Los archivos que se modificaron en el paso 4 también se modifican localmente. |
| Solución de enlace que nunca estuvo bajo control de código fuente | 1. Cree una carpeta vacía en el control de código fuente.<br />2. Cree un proyecto de cliente.<br />3. Abra el cuadro de diálogo **Cambiar control de código fuente** (**Archivo**, Control de **código fuente**, Cambiar control de **código fuente**).<br />4. Enlazar la solución a la ubicación vacía en el control de código fuente.<br />5. Hacer clic **OK** para cerrar el cuadro de diálogo **Cambiar control de código fuente.**<br />6. Haga clic en **Continuar con estos enlaces** en el cuadro de diálogo de confirmación.<br />7. Hacer clic **OK** en el cuadro de diálogo de advertencia si aparece. | Solución se agrega al control de código fuente.<br /><br /> La solución y el proyecto están desprotegidos. |
| Cancelar enlace | 1. Cree un proyecto.<br />2. Agregue la solución al control de código fuente.<br />3. Abra el cuadro de diálogo Cambiar control de código fuente.<br />4. Desenlazar todo.<br />5. Hacer clic **OK** para cerrar el cuadro de diálogo. Si este paso se realiza correctamente, continúe con el paso siguiente.<br />6. Vuelva a abrir el cuadro de diálogo **Cambiar control de código fuente.**<br />7. Enlazar a una ubicación no relacionada.<br />8. Haga clic en **Cancelar**. | `Result from Step 5:`<br /><br /> La solución ya no está bajo control de código fuente<br /><br /> `Result from Step 8:`<br /><br /> La solución todavía NO está bajo control de código fuente. |

### <a name="case-5b-unbind"></a>Caso 5b: Desenlazar
 Desenlazar quita la información de control de código fuente de los proyectos y su solución. Los proyectos y la solución afectados se basan en una combinación de selección de usuario y cómo se agregaron los elementos al control de código fuente.

|Acción|Pasos de prueba|Resultados esperados para verificar|
|------------|----------------|--------------------------------|
|Desenlazar solución que contiene un sistema de archivos o un proyecto web IIS local y un proyecto de cliente|1. Cree un sistema de archivos o un proyecto web IIS local.<br />2. Agregue la solución al control de código fuente.<br />3. Agregue un nuevo proyecto de cliente a la solución.<br />4. Acepte La desprotección de la solución si se le solicita.<br />5. Abra el cuadro de diálogo **Cambiar control de código fuente.**<br />6. Haga clic en **Desvincular**.<br />7. Hacer clic **OK** para cerrar el cuadro de diálogo.<br />8. Intente comprobar la solución, proyecto, elementos de solución, elementos del proyecto.|La solución y los proyectos NO están bajo control de código fuente.<br /><br /> Los comandos del menú Control de código fuente no aparecen.|
|Cancelar desvincular|1. Cree un proyecto.<br />2. Agregue la solución al control de código fuente.<br />3. Abra el cuadro de diálogo **Cambiar control de código fuente.**<br />4. Haga clic en **Desenlazar todo**.<br />5. Haga clic en **Cancelar**.|La solución está bajo control de código fuente.|

### <a name="case-5c-rebind"></a>Caso 5c: Reenlazar
 Rebind es simplemente una combinación de desenlazar y enlazar: el proceso de volver a enlazar un proyecto o solución que anteriormente estaba bajo control de código fuente y no estaba enlazado.

|Acción|Pasos de prueba|Resultados esperados para verificar|
|------------|----------------|--------------------------------|
|Vuelva a enlazar la solución y los proyectos sin cerrar el cuadro de diálogo **Cambiar control de código fuente**|1. Cree un proyecto.<br />2. Agregue la solución al control de código fuente.<br />3. Abra el cuadro de diálogo **Cambiar control de código fuente.**<br />4. Haga clic en **Desvincular**.<br />5. Seleccione todas las filas.<br />6. Haga clic en **Enlazar**.<br />7. Hacer clic **OK** para cerrar el cuadro de diálogo **Cambiar control de código fuente.**<br />8. Acepte el pago si se le solicita.|La solución y el proyecto están bajo control de código fuente.|
|Volver a enlazar el proyecto solo sin cerrar el cuadro de diálogo **Cambiar control de código fuente**|1. Cree un proyecto.<br />2. Agregue solo el proyecto al control de código fuente mediante (Control de código fuente de >de archivo >Agregar proyectos seleccionados al control de código fuente.<br />3. Abra el cuadro de diálogo Cambiar control de código fuente.<br />4. Desenlazar sólo el proyecto.<br />5. Enlazar sólo el proyecto.|La solución permanece incontrolada.<br /><br /> El proyecto permanece controlado.|
|Vuelva a enlazar la solución solo sin cerrar el cuadro de diálogo **Cambiar control de código fuente**|1. Cree un proyecto.<br />2. Agregue solo la solución al control de código fuente mediante (**File**, **Source Control**, Add Selected Projects to Source **Control**.<br />3. Abra el cuadro de diálogo **Cambiar control de código fuente.**<br />4. Desenlazar solo la solución (No cerrar **Cambiar control de código fuente** cuadro de diálogo.)<br />5. Enlazar sólo la solución.<br />6. Hacer clic **OK** para cerrar el cuadro de diálogo.<br />7. Echa un vistazo a los elementos de solución y solución (si los hay.)|La solución permanece controlada.<br /><br /> El proyecto permanece incontrolado.|
|Reenlazar solución/proyecto solo cuando se encuentra en el mismo directorio|1. Cree un proyecto.<br />2. Agregue solo el proyecto al control de código fuente mediante (**Archivo**, **Control de código fuente**, Agregar proyectos **seleccionados al Control de código fuente**.<br />3. Cierre la solución.<br />4. Cree una nueva solución con al menos dos proyectos.<br />5. Agregue la solución al control de código fuente.<br />6. Agregue el proyecto creado en el paso 1 desde el control de código fuente.<br />7. Acepte la compra de la solución si se le solicita.<br />8. Compruebe toda la solución.<br />9. Abra el cuadro de diálogo **Cambiar control de código fuente.**<br />10. Seleccione el proyecto agregado (desde el paso 6) y haga clic en **Desvincular**.<br />11. Hacer clic **OK** para cerrar el cuadro de diálogo.<br />12. Acepte la compra si se le solicita.<br />13. Vuelva a abrir el cuadro de diálogo **Cambiar control de código fuente.**<br />14. Seleccione el proyecto agregado (desde el paso 6) y haga clic en **Enlazar**.<br />15. Seleccione la ubicación original.|La solución y los proyectos permanecen controlados.|

## <a name="see-also"></a>Vea también
- [Guía de pruebas para los complementos de control de código fuente](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)
