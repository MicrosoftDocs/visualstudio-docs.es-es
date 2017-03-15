---
title: "Cuadro de di&#225;logo Esquemas XML | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0271fa26-2205-49bd-96e0-ae1441571808
caps.latest.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 2
---
# Cuadro de di&#225;logo Esquemas XML
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

El cuadro de diálogo **Esquemas XML** se usa para seleccionar los esquemas del lenguaje de definición de esquemas XML \(XSD\) que se van a asociar con un documento XML.Podrá seleccionar un esquema de la caché de esquema o especificar un esquema que no está ubicado en la caché.Los esquemas seleccionados se consideran parte de un conjunto de esquemas.IntelliSense y la validación de documentos XML usan el conjunto de esquemas.  
  
 Para tener acceso al cuadro de diálogo **Esquemas XML** haga clic en el botón **Esquemas** de la ventana propiedades del documento o seleccione **Esquemas** en el menú **XML**.  
  
## Lista de UIElement  
 **Usar**  
 Seleccione cómo usar el esquema XML.  
  
-   **Automático**.Aunque este esquema no se utiliza en el documento actual, está disponible para la asociación automática.Si el documento XML declara un espacio de nombres que coincide con el `targetNamespace` de este esquema, el esquema se asociará automáticamente y se incluirá en el conjunto de esquemas.  
  
-   **Utilizar este esquema**.El documento actual está utilizando este esquema.El usuario ha hecho clic en la columna para usar explícitamente este esquema, o el esquema estaba asociado automáticamente a una coincidencia con `targetNamespace`.  
  
-   **No utilizar esquemas seleccionados**.El documento actual no utiliza este esquema, aunque haya una coincidencia del esquema con `targetNamespace`.Esta configuración puede ser útil para resolver conflictos cuando hay más de una versión del mismo esquema en la solución o caché de esquema.  
  
 **Espacio de nombres de destino**  
 Muestra el espacio de nombres de destino asociado con el esquema XML.  
  
 **Nombre de archivo**  
 Muestra el nombre de archivo del esquema XML.  
  
 **Agregar**  
 Abre el cuadro de diálogo **Abrir esquema XSD**, que permite seleccionar otros esquemas y agregarlos al conjunto de esquemas.Al agregar un esquema al conjunto de esquemas, el valor de la columna **Usar** se establece en **Utilizar este esquema**.  
  
 **Quitar**  
 Quita el esquema seleccionado actualmente del conjunto de esquemas.Esto supone quitar el esquema de la caché de esquema en memoria, pero no del sistema de archivos.  
  
## Vea también  
 [Componentes del Editor XML](../xml-tools/xml-editor-components.md)   
 [Cómo: Seleccionar los esquemas XML que se van a usar](../xml-tools/how-to-select-the-xml-schemas-to-use.md)   
 [Caché de esquema](../xml-tools/schema-cache.md)