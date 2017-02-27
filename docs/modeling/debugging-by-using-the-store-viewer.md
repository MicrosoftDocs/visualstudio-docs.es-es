---
title: "Depurar con el visor de almac&#233;n | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Lenguaje específico de dominio, almacén"
  - "Lenguaje específico de dominio, visor de almacén"
ms.assetid: 0178db2e-ae99-4ed3-9b87-8620fa9fa8e4
caps.latest.revision: 17
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 17
---
# Depurar con el visor de almac&#233;n
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Con el visor de almacén, puede examinar el estado *de un almacén* utilizado por [!INCLUDE[dsl](../modeling/includes/dsl_md.md)].  El visor de almacén muestra todos los elementos del modelo de dominio que están en un almacén concreto, junto con propiedades de elementos y vínculos entre los elementos.  
  
## Visor almacenado que abra  
 Cuando está en la compilación experimental de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], detenga el código en un punto de interrupción en una instancia del almacén contiene la información del modelo. A continuación, abra el visor de almacén escribiendo el comando siguiente en la ventana de  **Inmediato**:  
  
```  
Microsoft.VisualStudio.Modeling.Diagnostics.StoreViewer.Show(mystore);  
```  
  
> [!NOTE]
>  Debe reemplazar `mystore` con el nombre de la instancia del almacén.  Además, si agrega el espacio de nombres al código, puede escribir el comando para mostrar el visor almacenado sin todo el espacio de nombres:  
>   
>  `using Microsoft.VisualStudio.Modeling.Diagnostics;`  
>   
>  `…`  
>   
>  `StoreViewer.Show(mystore);`  
  
 El método `Show` tiene varias sobrecargas.  Puede especificar una instancia de un almacén o una partición como parámetro.  
  
 Como alternativa, puede colocar la línea de código que muestra el visor de almacén en cualquier parte del código donde es el parámetro que se pasa a `Show` el método en el ámbito.  Esta acción muestra el visor de almacén cuando la línea de código se ejecuta como una instantánea del contenido del almacén.  
  
### Con el visor almacenado  
 Cuando se abre el visor store, una ventana no modal de Windows Forms se, como muestra la siguiente ilustración.  
  
 ![](../modeling/media/storeviewer2.png "storeviewer2")  
Visor de almacén  
  
 El visor de almacén tiene tres paneles: el panel izquierdo, panel derecho superior, y panel inferior derecho.  El panel izquierdo es una vista de árbol de los tipos en el miembro de `DomainDataDirectory` de un almacén.  Si expande el nodo del elemento y haga clic en un elemento, las propiedades del elemento aparecen en el panel derecho superior.  Si el elemento está vinculado a otros elementos, elementos adicionales aparecen en el panel inferior derecho.  Si hace doble clic en un elemento en el panel inferior derecho, el elemento aparecerá resaltada en el panel izquierdo.  
  
## Vea también  
 [Navegar y actualizar un modelo en el código del programa](../modeling/navigating-and-updating-a-model-in-program-code.md)