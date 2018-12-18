---
title: Ver los valores de datos en sugerencias de datos en el editor de código | Documentos de Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], DataTips
- DataTips tool
ms.assetid: ffa7bd18-439b-4685-a9b3-c7884b5de41f
caps.latest.revision: 41
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 37fc58a68f8cf482ac6a2bbab3ecb47c28d60904
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51799449"
---
# <a name="view-data-values-in-data-tips--in-the-code-editor"></a>Ver valores de datos en sugerencias de datos en el editor de código
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La Información sobre datos es una manera útil de ver información sobre las variables del programa durante la depuración. La Información sobre datos funciona únicamente en modo de interrupción y únicamente con las variables que están dentro del actual ámbito de ejecución.  
  
 En [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)], información sobre datos se puede anclar en una ubicación específica en un archivo de origen, o puede flotar encima de todo [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] windows.  
  
### <a name="to-display-a-datatip-in-break-mode-only"></a>Para mostrar la Información sobre datos solo en modo de interrupción  
  
1. En una ventana de código fuente, coloque el puntero del mouse sobre cualquier variable en el ámbito actual.  
  
    Aparece la Información sobre datos.  
  
   > [!NOTE]
   >  Las informaciones sobre datos siempre se evalúan en el contexto en el que se suspende la ejecución, y no en el que el cursor se mantiene sobre un elemento. Si mantiene el cursor sobre una variable en otra función con el mismo nombre que una variable que está en el contexto actual, el valor de la variable de la otra función se mostrará como el valor de la variable del contexto actual.  
  
2. La Información sobre datos desaparece al quitar el puntero del mouse. Para anclar la información sobre datos de modo que permanezca abierta, haga clic en el **anclar a origen** icono, o  
  
   - Haga doble clic en una variable, a continuación, haga clic en **anclar a origen**.  
  
     La Información sobre datos se cierra cuando la sesión de depuración finaliza.  
  
### <a name="to-unpin-a-datatip-and-make-it-float"></a>Desanclar la Información sobre datos y dejar que flote  
  
-   En una información sobre datos anclada, haga clic en el **Desanclar del origen** icono.  
  
     El icono pasa a la posición desanclada. La Información sobre datos flota ahora sobre las ventanas abiertas. La Información sobre datos que flota se cierra cuando la sesión de depuración finaliza.  
  
### <a name="to-repin-a-floating-datatip"></a>Para volver a anclar una Información sobre datos flotante  
  
-   En una Información sobre datos, haga clic en el icono de anclaje.  
  
     El icono pasa a la posición anclada. Si la Información sobre datos está fuera de una ventana de código fuente, el icono está deshabilitado y no se puede anclar.  
  
### <a name="to-close-a-datatip"></a>Para cerrar una Información sobre datos  
  
-   Coloque el puntero del mouse sobre una información sobre datos y, a continuación, haga clic en el **cerrar** icono.  
  
### <a name="to-close-all-datatips"></a>Para cerrar toda la Información sobre datos  
  
-   En el **depurar** menú, haga clic en **borrar todas las sugerencias de datos**.  
  
### <a name="to-close-all-datatips-for-a-specific-file"></a>Para cerrar toda la información sobre datos de un archivo concreto  
  
-   En el **depurar** menú, haga clic en **borrar todos los información sobre datos anclada a** *archivo*.  
  
## <a name="expanding-and-editing-information"></a>Expandir y editar información  
 Con la Información sobre datos, se puede expandir una matriz, una estructura o un objeto para ver sus miembros. También se puede editar el valor de una variable de una Información sobre datos.  
  
#### <a name="to-expand-a-variable-to-see-its-elements"></a>Para expandir una variable y ver sus elementos  
  
-   En una información sobre datos, coloque el puntero del mouse sobre el **+** inicio de sesión que precede al nombre de variable.  
  
     La variable se expande y se muestran sus elementos en forma de árbol.  
  
     Cuando la variable está expandida, puede utilizar las teclas de dirección en el teclado para desplazarse de arriba abajo. También puede utilizar el mouse.  
  
#### <a name="to-edit-the-value-of-a-variable-using-a-datatip"></a>Para modificar el valor de una variable mediante la Información sobre datos  
  
1.  En una Información sobre datos, haga clic en el valor. En los valores de solo lectura, no está habilitado.  
  
2.  Escriba el nuevo valor y presione ENTRAR.  
  
## <a name="making-a-datatip-transparent"></a>Configurar una Información sobre datos como transparente  
 Si desea ver el código que está detrás de una Información sobre datos, puede configurar temporalmente dicha información como transparente. Esto no se aplica a la información sobre datos cuando está anclada o flota.  
  
#### <a name="to-make-a-datatip-transparent"></a>Para configurar una Información sobre datos como transparente  
  
-   En una Información sobre datos, presione CTRL.  
  
     La Información sobre datos permanecerá transparente mientras mantenga presionada la tecla CTRL.  
  
## <a name="visualizing-complex-data-types"></a>Visualizar tipos de datos complejos  
 Si aparece un icono de lupa junto a un nombre de variable en una información sobre datos, uno o varios [crear los visualizadores personalizados](../debugger/create-custom-visualizers-of-data.md) están disponibles para las variables de ese tipo de datos. Los visualizadores se pueden utilizar para mostrar la información de manera más significativa, normalmente de forma gráfica.  
  
#### <a name="to-view-the-contents-of-a-variable-using-a-visualizer"></a>Para ver el contenido de una variable mediante un visualizador  
  
-   Haga clic en el icono de lupa para seleccionar el visualizador predeterminado del tipo de datos.  
  
     O bien  
  
     Haga clic en la flecha emergente junto al visualizador para seleccionar una lista emergente de visualizadores adecuados para el tipo de datos.  
  
     Un visualizador muestra la información.  
  
## <a name="adding-information-to-a-watch-window"></a>Agregar información a una ventana Inspección  
 Si desea seguir examinando una variable, puede agregar la variable a la **inspección** ventana desde una información sobre datos.  
  
#### <a name="to-add-a-variable-to-the-watch-window"></a>Para agregar una variable a la ventana Inspección  
  
-   Haga clic en una información sobre datos y, a continuación, haga clic en **Agregar inspección**.  
  
     La variable se agrega a la **inspección** ventana. Si usa una versión que admite varias **inspección** windows, la variable se agrega a **Inspección 1.**  
  
## <a name="importing-and-exporting-datatips"></a>Importar y exportar Información sobre datos  
 Puede exportar Información sobre datos a un archivo XML, que puede compartir con un colega o modificar con un editor de texto.  
  
#### <a name="to-export-datatips"></a>Para exportar información sobre datos  
  
1.  En el menú Depurar, haga clic en **exportar información sobre datos**.  
  
     El **exportar información sobre datos** aparece el cuadro de diálogo.  
  
2.  Usar técnicas de archivo estándar para navegar hasta la ubicación donde desea guardar el archivo XML, escriba un nombre para el archivo en el **nombre de archivo** cuadro y, a continuación, haga clic en **Aceptar**.  
  
#### <a name="to-import-datatips"></a>Para importar información sobre datos  
  
1.  En el menú Depurar, haga clic en **importar información sobre datos**.  
  
     El **importar información sobre datos** aparece el cuadro de diálogo.  
  
2.  Utilice el cuadro de diálogo para buscar el archivo XML que desea abrir y haga clic en **Aceptar**.  
  
## <a name="see-also"></a>Vea también  
 [Visualización de datos en el depurador](../debugger/viewing-data-in-the-debugger.md)   
 [Cómo: usar el cuadro de diálogo Inspección rápida](http://msdn.microsoft.com/library/ffaee1dd-e5ce-4ef2-9401-d28329398867)   
 [Crear visualizadores personalizados](../debugger/create-custom-visualizers-of-data.md)   
 [Cómo: cambiar el formato numérico de Windows del depurador](http://msdn.microsoft.com/library/cd593847-a625-411d-a430-b798346ef18f)



