---
title: "Tutorial de configuración de Visual Studio Tools para Unity Azure| Microsoft Docs"
ms.custom: 
ms.date: 10/19/2017
ms.reviewer: crdun
ms.suite: 
ms.technology: tgt-pltfrm-cross-plat
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: FFE17FC6-0B47-4A00-A125-01BD49E3873C
author: dantogno
ms.author: v-davian
manager: crdun
ms.workload:
- azure
- unity
ms.openlocfilehash: ba9de2e6af5c066e83b75576f9b104f20908aec6
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="create-easy-tables"></a>Crear tablas fáciles

Ahora que tiene una aplicación móvil en Azure con Easy Tables inicializado, es hora de crear las tablas que harán un seguimiento de los datos enviados desde un juego de Unity.

## <a name="setup-the-crash-heatmap-table"></a>Configurar la tabla de mapa térmico de choques

1. En el portal de Azure, haga clic en Todos los recursos y seleccione la aplicación móvil que ha configurado para Easy Tables en los pasos anteriores.

  ![Seleccionar aplicación móvil](media/vstu_azure-setup-table-schema-image1.png)

2. Desplácese hacia abajo hasta el encabezado **MOBILE** (MÓVIL) y seleccione **Easy Tables** (Tablas fáciles). Ya no debería haber ningún aviso acerca de cómo inicializar la aplicación para Easy Tables.  

  ![Seleccione Tablas fáciles](media/vstu_azure-setup-table-schema-image2.png)

3. Haga clic en el botón **Agregar**.

  ![Hacer clic en Agregar](media/vstu_azure-setup-table-schema-image3.png)

4. Asigne el nombre “**CrashInfo**” a la tabla y haga clic en **Aceptar**. Deje el resto de opciones con su configuración predeterminada.

  > [!WARNING]
  > Este nombre debe coincidir con el nombre de la clase del modelo de datos creado más adelante en el tutorial.

  ![Asignar un nombre y hacer clic en Aceptar](media/vstu_azure-setup-table-schema-image4.png)

5. Se mostrará una notificación cuando se haya creado la nueva tabla.

> [!NOTE]
> Con Easy Tables, en realidad el esquema de tabla se crea dinámicamente a medida que se agregan datos. Esto significa que no es necesario configurar manualmente las columnas de datos adecuadas durante este paso.

## <a name="setup-the-leaderboard-table"></a>Configurar la tabla de clasificación

1. Vuelva a la hoja de Easy Tables y haga clic en **Agregar** para agregar una segunda tabla.

  ![Agregar una segunda tabla](media/vstu_azure-setup-table-schema-image10.png)

2. Asigne el nombre “**HighScoreInfo**” a la segunda tabla y haga clic en **Aceptar**. Deje el resto de opciones con su configuración predeterminada.

  > [!WARNING]
  > Este nombre debe coincidir con el nombre de la clase del modelo de datos creado más adelante en el tutorial.

  ![Asignar un nombre y hacer clic en Aceptar](media/vstu_azure-setup-table-schema-image11.png)

3. Se mostrará una notificación cuando se haya creado la nueva tabla.


## <a name="next-step"></a>Paso siguiente

* [Preparación del entorno de desarrollo](visual-studio-tools-for-unity-azure-prepare.md)
