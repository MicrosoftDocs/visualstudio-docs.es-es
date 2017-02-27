---
title: "Personalizar el Explorador de modelos | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.dsltools.dsldesigner.explorerbehavior"
helpviewer_keywords: 
  - "Herramientas de lenguajes específicos de dominio, Explorador de lenguajes específicos de dominio"
ms.assetid: d2926444-9408-41d8-a27e-3fd0c416f9ac
caps.latest.revision: 20
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 20
---
# Personalizar el Explorador de modelos
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Puede cambiar el aspecto y el comportamiento del explorador para el diseñador específico del lenguaje como sigue:  
  
-   Cambie el título de la ventana.  
  
-   Cambie el icono de la pestaña.  
  
-   Cambiar iconos para los nodos.  
  
-   Ocultar nodos.  
  
## Cambiar el título de la ventana  
 Para cambiar el título de la ventana del explorador generado, **Comportamiento del Explorador** seleccione en **Explorador ADSL**y, en la ventana de **Propiedades** , establezca la propiedad de **Título** al título que desee.  
  
## Cambiar el icono tab.  
 Para cambiar el icono de la pestaña del explorador, utilice un icono 16x16\-pixel en un archivo .bmp.  Coloque el archivo de icono en \\DslPackage\\Resources\\ folder, and then change the file name to ModelExplorerToolWindowBitmaps .bmp.  Por ejemplo, puede cambiar el archivo de icono de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] setup.ico el formato .bmp y cambiarle el nombre a DSLLanguageName \\DslPackage\\Resources\\ModelExplorerToolWindowBitmaps .bmp.  El diseñador generado mostrará este icono en la ficha explorador cuando se acopla así como **Explorador de soluciones**.  
  
## Iconos personalizados en el Explorador Nodos  
 Puede personalizar los nodos del explorador utilizando valores de nodo del explorador.  el procedimiento siguiente muestra cómo agregar un icono a un nodo.  
  
#### Para agregar un icono a un nodo del explorador  
  
1.  Cree una solución de [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] mediante la plantilla de solución de flujo de la tarea.  
  
2.  Coloque un archivo .bmp que contiene un icono 16x16\-pixel en la carpeta de **DSL \\Resources** en la solución.  
  
3.  En **Explorador ADSL**, haga clic con el botón secundario **Comportamiento del Explorador** y haga clic en **Agregue los nuevos valores de nodo del Explorador**.  
  
     Un nodo de **ExplorerNodeSettings** aparece bajo el nodo de **Valores personalizados de nodo** .  
  
4.  **ExplorerNodeSettings**seleccione y, en la ventana de **Propiedades** , establezca **class** a **actor**.  
  
5.  Establezca **Icono para mostrar** a la ruta de acceso del archivo de icono.  
  
6.  Transformar todas las plantillas y, a continuación compile y ejecute la solución.  
  
7.  En el diseñador generado, abra el diagrama de ejemplo.  
  
     El Explorador debe mostrar tres nodos de **actor** que tienen el icono.  
  
> [!NOTE]
>  Si ha establecido un icono de nodo para cualquier elemento que se muestre en el explorador generado, todos los nodos del explorador mostrará el icono.  Si no se ha establecido ningún icono, los nodos mostrará el icono predeterminado.  
  
## Cambiando el nombre mostrado en un Explorador Node  
 Puede cambiar el modo en que los nombres de los elementos de modelo se muestran en el explorador.  El siguiente procedimiento muestra cómo mostrar el nombre de la tarea que hace referencia un comentario en el nodo de comentario.  
  
#### Para mostrar una propiedad  
  
1.  Abra la solución que creó en el procedimiento anterior.  
  
2.  Asegúrese de que las referencias de comentario una sola clase de dominio estableciendo la multiplicidad del rol con el nombre de propiedad **asuntos** a 0..1.  el nombre de propiedad debe convertirse en **Subject**, y el nombre de la relación debe convertirse en **CommentReferencesSubject**.  
  
3.  En **Explorador ADSL**, haga clic con el botón secundario **Comportamiento del Explorador** y haga clic en **Agregue los nuevos valores de nodo del Explorador**.  
  
     Un nodo de **ExplorerNodeSettings** aparece bajo el nodo de **Valores personalizados de nodo** .  
  
4.  **ExplorerNodeSettings**seleccione y, en la ventana de **Propiedades** , establezca **class** a **comentario**.  
  
5.  Haga clic con el botón secundario en el nodo de **comentario** , y haga clic en **Agregue la nueva ruta de acceso de propiedad**.  
  
     Un nuevo nodo aparece denominado **Propiedad mostrada**.  
  
6.  **Propiedad mostrada**seleccione y, en la ventana de **Propiedades** , haga clic en el campo de Valor de **Ruta de acceso a la propiedad**.  **comentario**seleccione, a continuación **CommentReferencesSubject**, entonces **Elemento dinámico**.  La ruta resultante debe ser similar a **CommentReferencesSubject.Subject\/\!Subject**.  
  
7.  En el campo de Valor de **Propiedad**, seleccione **Nombre**.  
  
8.  Transformar todas las plantillas y, a continuación compile y ejecute la solución.  
  
9. En el diseñador generado, abra el diagrama de ejemplo.  
  
10. Dibuje **Conector de comentario** entre el elemento comentario y el elemento de **Task1** en el diagrama.  
  
     El nodo del Explorador debe mostrar el comentario como **Task1**.  
  
## ocultar nodos  
 Puede ocultar un nodo en el explorador agregando la ruta al nodo de **Nodos ocultos** de **Explorador ADSL**.  El siguiente procedimiento muestra cómo ocultar nodos de comentario.  
  
#### Para ocultar un nodo del explorador  
  
1.  Abra la solución que creó en el procedimiento anterior.  
  
2.  En **Explorador ADSL**, haga clic con el botón secundario **Comportamiento del Explorador** y haga clic en **Agregue la nueva ruta de dominio**.  
  
     un nodo de **Ruta de acceso del dominio** aparece bajo **Nodos ocultos**.  
  
3.  **Ruta de acceso del dominio**seleccione y, en la ventana de **Propiedades** , haga clic en el campo de Valor de **definición de ruta**.  **FlowGraph**seleccione, a continuación **FlowGraphHasComments**.  La ruta resultante debe ser similar a **FlowGraphHasComments.Comments**  
  
4.  Transformar todas las plantillas y, a continuación compile y ejecute la solución.  
  
5.  En el diseñador generado, abra el diagrama de ejemplo.  
  
     El explorador debe mostrar un solo nodo de **actores** , y no debe mostrar el nodo de **Comentarios** .  
  
## Vea también  
 [Domain\-Specific Language Tools Glossary](http://msdn.microsoft.com/es-es/ca5e84cb-a315-465c-be24-76aa3df276aa)