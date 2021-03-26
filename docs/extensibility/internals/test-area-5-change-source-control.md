---
title: 'Área de prueba 5: cambiar control de código fuente | Microsoft Docs'
description: Este área de prueba del complemento de control de código fuente cubre el cambio del control de código fuente mediante el comando Cambiar control de código fuente.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], changing
- source control plug-ins, changing source control
ms.assetid: fdf09e00-108c-4d51-bbd5-72452d52a490
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 44647781b8f7605a59fba5d9249b6a7165c0e27e
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105073409"
---
# <a name="test-area-5-change-source-control"></a>Área de prueba 5: Cambio del control de código fuente
Este área de prueba del complemento de control de código fuente cubre el cambio del control de código fuente mediante el comando **Cambiar control de código fuente** .

 El comando **Cambiar control de código fuente** proporciona cuatro funciones básicas para el usuario:

- **Volver**

   Permite al usuario establecer o restablecer un vínculo de control de código fuente entre una solución/proyecto y el almacén de versiones.

- **Desenlazar**

   Quita un proyecto o solución del control de código fuente en cada conexión.

- **Conectar/desconectar:**

  Alterna el estado conectado o sin conexión de la solución controlada, que se trata en el área 3. Para obtener más información, vea [área de prueba 3: desproteger/deshacer la desprotección](../../extensibility/internals/test-area-3-check-out-undo-checkout.md).

## <a name="command-menu-access"></a>Acceso al menú de comandos
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]En los casos de prueba se usa la siguiente ruta de acceso del menú del entorno de desarrollo integrado.

 Cambiar control de código fuente:**archivo**, **control de código fuente**, **Cambiar control de código fuente**.

## <a name="test-cases"></a>Casos de prueba
 Los siguientes son casos de prueba específicos para el área de prueba del comando **Cambiar control de código fuente** .

### <a name="case-5a-bind"></a>Caso 5a: Bind
 Bind permite al usuario agregar información de control de código fuente a los proyectos y soluciones seleccionados. Normalmente, se pide al usuario que identifique un proyecto en el control de código fuente al que se van a agregar. El usuario no puede crear un nuevo proyecto en el control de código fuente como parte de esta operación (contraste con agregar a control de código fuente).

| Acción | Pasos de prueba | Resultados esperados que se van a comprobar |
| - | - | - |
| Enlazar a una ubicación vacía | 1. cree un proyecto.<br />2. Agregue la solución al control de código fuente.<br />3. abrir el cuadro de diálogo **Cambiar control de código fuente** (**archivo**, **control de código fuente**, **Cambiar control de código fuente**).<br />4. Haga clic en **Desenlazar**.<br />5. acepte el cuadro de diálogo de ADVERTENCIA Si aparece.<br />6. seleccionar todos los elementos.<br />7. Haga clic en **enlazar**.<br />8. Busque una ubicación vacía en un almacén de control de código fuente.<br />9. Haga clic en **Aceptar** para cerrar el cuadro de diálogo **Cambiar control de código fuente** .<br />10. Haga clic en **continuar con estos enlaces** en el cuadro de diálogo de confirmación.<br />11. Haga clic en **Aceptar** en el cuadro de diálogo de advertencia, si aparece.<br />12. Proteja todo. Si este paso se realiza correctamente, continúe con el paso siguiente.<br />13. Abra la solución desde el control de código fuente a una nueva ubicación. | `Result from Step 12:`<br /><br /> La solución y el proyecto se enlazan y se escriben en el nuevo destino en el almacén de versiones.<br /><br /> Los archivos de solución y proyecto están protegidos.<br /><br /> La jerarquía del proyecto de almacén de versiones coincide con la jerarquía de carpetas del proyecto en el disco.<br /><br /> `Result from Step 13:`<br /><br /> Se descargan todos los elementos de proyecto. |
| Enlazar con la ubicación que está sincronizada con el cliente | 1. cree un proyecto.<br />2. Agregue la solución al control de código fuente.<br />3. cree un duplicado de la solución y el proyecto en el almacén de versiones (compartir y bifurcar si se usa [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)] ).<br />4. abrir el cuadro de diálogo **Cambiar control de código fuente** (**archivo**, **control de código fuente**, **Cambiar control de código fuente**).<br />5. Desenlazar todo.<br />6. Haga clic en **Aceptar** para cerrar el cuadro de diálogo **Cambiar control de código fuente** .<br />7. Vuelva a abrir el cuadro de diálogo **Cambiar control de código fuente** .<br />8. seleccionar todo.<br />9. Haga clic en **enlazar**.<br />10. vaya a la ubicación bifurcada de la solución y el proyecto (del paso 3)<br />11. Haga clic en **Aceptar** para cerrar el cuadro de diálogo **Cambiar control de código fuente** .<br />12. obtener la última versión de forma recursiva para todos los elementos. | El contenido del archivo después de la obtención es el mismo que antes de la obtención. |
| Enlazar a la ubicación que no está sincronizada con el cliente | 1. cree un proyecto.<br />2. Agregue la solución al control de código fuente.<br />3. cree un duplicado de la solución y el proyecto en el almacén de versiones (compartir y bifurcar si se usa [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)] ).<br />4. modifique los archivos del proyecto bifurcado en el almacén de versiones.<br />5. abrir el cuadro de diálogo **Cambiar control de código fuente** (**archivo**, **control de código fuente**, **Cambiar control de código fuente**).<br />6. Desenlazar todo.<br />7. Haga clic en **Aceptar** para cerrar el cuadro de diálogo **Cambiar control de código fuente** .<br />8. Vuelva a abrir el cuadro de diálogo **Cambiar control de código fuente** .<br />9. seleccionar todo.<br />10. Haga clic en **enlazar**.<br />11. vaya a la ubicación bifurcada para la solución y el proyecto.<br />12. Haga clic en **Aceptar** para cerrar el cuadro de diálogo **Cambiar control de código fuente** .<br />13. acepte el cuadro de diálogo de ADVERTENCIA Si aparece.<br />14. obtener la última versión recursiva para todos los elementos. | Los archivos que se modificaron en el paso 4 también se modifican de forma local. |
| Solución de enlace que nunca estaba bajo control de código fuente | 1. cree una carpeta vacía en el control de código fuente.<br />2. cree un proyecto de cliente.<br />3. abrir el cuadro de diálogo **Cambiar control de código fuente** (**archivo**, **control de código fuente**, **Cambiar control de código fuente**).<br />4. enlazar la solución a una ubicación vacía en el control de código fuente.<br />5. Haga clic en **Aceptar** para cerrar el cuadro de diálogo **Cambiar control de código fuente** .<br />6. Haga clic en **continuar con estos enlaces** en el cuadro de diálogo de confirmación.<br />7. Haga clic en **Aceptar** en el cuadro de diálogo de advertencia, si aparece. | La solución se agrega al control de código fuente.<br /><br /> La solución y el proyecto están desprotegidos. |
| Cancelar enlace | 1. cree un proyecto.<br />2. Agregue la solución al control de código fuente.<br />3. Abra el cuadro de diálogo Cambiar control de código fuente.<br />4. Desenlazar todo.<br />5. Haga clic en el botón **Aceptar** para cerrar el cuadro de diálogo. Si este paso se realiza correctamente, continúe con el paso siguiente.<br />6. Vuelva a abrir el cuadro de diálogo **Cambiar control de código fuente** .<br />7. enlace a una ubicación no relacionada.<br />8. Haga clic en **Cancelar**. | `Result from Step 5:`<br /><br /> La solución ya no está bajo control de código fuente<br /><br /> `Result from Step 8:`<br /><br /> La solución todavía no está bajo control de código fuente. |

### <a name="case-5b-unbind"></a>Caso 5b: Unbind
 Unbind quita la información de control de código fuente de los proyectos y su solución. Los proyectos y la solución afectados se basan en una combinación de selección de usuario y en cómo se agregaron los elementos al control de código fuente.

|Acción|Pasos de prueba|Resultados esperados que se van a comprobar|
|------------|----------------|--------------------------------|
|Desenlazar la solución que contiene un sistema de archivos o un proyecto Web de IIS local y un proyecto de cliente|1. cree un sistema de archivos o un proyecto Web de IIS local.<br />2. Agregue la solución al control de código fuente.<br />3. Agregue un nuevo proyecto de cliente a la solución.<br />4. acepte la desprotección de la solución si se le solicita.<br />5. Abra el cuadro de diálogo **Cambiar control de código fuente** .<br />6. Haga clic en **Desenlazar**.<br />7. Haga clic en **Aceptar** para cerrar el cuadro de diálogo.<br />8. intente desproteger la solución, el proyecto, los elementos de la solución, los elementos de proyecto.|La solución y los proyectos no están bajo control de código fuente.<br /><br /> Los comandos de menú de control de código fuente no aparecen.|
|Cancelar desenlace|1. cree un proyecto.<br />2. Agregue la solución al control de código fuente.<br />3. Abra el cuadro de diálogo **Cambiar control de código fuente** .<br />4. Haga clic en **Desenlazar todo**.<br />5. Haga clic en **Cancelar**.|La solución está bajo control de código fuente.|

### <a name="case-5c-rebind"></a>Caso 5c: Reenlace
 Reenlazar es simplemente una combinación de desenlace y enlace: el proceso de volver a enlazar un proyecto o una solución que anteriormente estaba bajo control de código fuente y era independiente.

|Acción|Pasos de prueba|Resultados esperados que se van a comprobar|
|------------|----------------|--------------------------------|
|Volver a enlazar la solución y los proyectos sin cerrar el cuadro de diálogo **Cambiar control de código fuente**|1. cree un proyecto.<br />2. Agregue la solución al control de código fuente.<br />3. Abra el cuadro de diálogo **Cambiar control de código fuente** .<br />4. Haga clic en **Desenlazar**.<br />5. seleccionar todas las filas.<br />6. Haga clic en **enlazar**.<br />7. Haga clic en **Aceptar** para cerrar el cuadro de diálogo **Cambiar control de código fuente** .<br />8. acepte la desprotección si se le solicita.|La solución y el proyecto están bajo control de código fuente.|
|Volver a enlazar el proyecto solo sin cerrar el cuadro de diálogo **Cambiar control de código fuente**|1. cree un proyecto.<br />2. agregar solo el proyecto al control de código fuente mediante (control de código fuente de >de archivo >agregar proyectos seleccionados al control de código fuente.<br />3. Abra el cuadro de diálogo Cambiar control de código fuente.<br />4. Desenlazar solo el proyecto.<br />5. enlazar solo el proyecto.|La solución permanece sin control.<br /><br /> El proyecto permanece controlado.|
|Reenlazar solución solo sin cerrar **Cambiar control de código fuente** (cuadro de diálogo)|1. cree un proyecto.<br />2. Agregue solo la solución al control de código fuente mediante (**archivo**, **control de código fuente**, **Agregar proyectos seleccionados al control de código fuente**.<br />3. Abra el cuadro de diálogo **Cambiar control de código fuente** .<br />4. Desenlazar solo la solución (no cierre el cuadro de diálogo **Cambiar control de código fuente** ).<br />5. enlazar solo la solución.<br />6. Haga clic en **Aceptar** para cerrar el cuadro de diálogo.<br />7. Consulte los elementos de la solución y la solución (si los hay).|La solución permanece controlada.<br /><br /> El proyecto permanece sin control.|
|Reenlazar solución/proyecto solo cuando está en el mismo directorio|1. cree un proyecto.<br />2. Agregue solo el proyecto al control de código fuente mediante (**archivo**, **control de código fuente**, **Agregar proyectos seleccionados al control de código fuente**.<br />3. Cierre la solución.<br />4. cree una nueva solución con al menos dos proyectos.<br />5. agregar la solución al control de código fuente.<br />6. Agregue el proyecto creado en el paso 1 desde el control de código fuente.<br />7. acepte la desprotección de la solución si se le solicita.<br />8. Proteja toda la solución.<br />9. Abra el cuadro de diálogo **Cambiar control de código fuente** .<br />10. Seleccione el proyecto agregado (del paso 6) y haga clic en **Desenlazar**.<br />11. Haga clic en **Aceptar** para cerrar el cuadro de diálogo.<br />12. acepte la desprotección si se le solicita.<br />13. Vuelva a abrir el cuadro de diálogo **Cambiar control de código fuente** .<br />14. Seleccione el proyecto agregado (del paso 6) y haga clic en **enlazar**.<br />15. Seleccione la ubicación original.|La solución y los proyectos permanecen controlados.|

## <a name="see-also"></a>Consulte también
- [Guía de pruebas para los complementos de control de código fuente](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)
