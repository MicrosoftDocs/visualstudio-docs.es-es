---
title: "C&#243;mo: Seleccionar los esquemas XML que se van a usar | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d6fda3ef-d465-4788-8514-2f2d528d658c
caps.latest.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 2
---
# C&#243;mo: Seleccionar los esquemas XML que se van a usar
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

El Editor XML proporciona una memoria caché de esquemas que está ubicada en el directorio %InstallDir%\\Xml\\Schemas.La caché de esquema incluye esquemas XML muy conocidos que se utilizan en IntelliSense y en la validación de documentos XML.  
  
 La propiedad de documento **Esquemas** se emplea para seleccionar uno o varios esquemas de lenguaje de definición de esquemas XML \(XSD\) que se usarán en la validación.Permite seleccionar esquemas de la caché de esquema o especificar un esquema que no está ubicado en la caché.  
  
 Los esquemas especificados se guardan en el archivo oculto de opciones del usuario de la solución \(.suo\), junto con todas las demás propiedades de documento XML.Por tanto, no es necesario que vuelva a escribir estos valores la próxima vez que abra la solución.  
  
> [!NOTE]
>  El editor puede realizar la validación mediante un esquema alineado o un esquema al que se haga referencia en el atributo `xsd:schemaLocation`.Para obtener más información, vea [Validación de documentos XML](../xml-tools/xml-document-validation.md).  
  
### Para seleccionar un esquema XML de la caché de esquema  
  
1.  Abra un archivo en el Editor XML.  
  
2.  En la ventana de propiedades del documento, haga clic en el botón del campo **Esquemas**.  
  
     Aparece el cuadro de diálogo **Esquemas XML**.En el cuadro de diálogo se muestran todos los esquemas con una extensión .xsd en la caché de esquema \(incluidos los esquemas a los que se hace referencia en el archivo catalog.xml\), así como los esquemas que se encuentren en la solución actual, que estén abiertos en Visual Studio, a los que se haga referencia en un atributo `xsd:schemaLocation` o a los que se haga referencia en la propiedad **Esquemas**.  
  
3.  Seleccione los esquemas que desea utilizar en la validación mediante una de las siguientes acciones:  
  
    -   Seleccione un esquema que aparece en el cuadro de diálogo **Esquemas XML**, haga clic en la columna **Usar** y, a continuación, seleccione **Utilizar este esquema**.  
  
     \-o\-  
  
    -   Seleccione varios esquemas que aparecen en el cuadro de diálogo **Esquemas XML**, haga clic con el botón secundario y seleccione **Utilizar este esquema**.  
  
4.  Haga clic en **Aceptar**.  
  
     La lista de esquemas seleccionados se copia de nuevo en la propiedad de documento **Esquemas**.  
  
### Para agregar un esquema XML a la caché de esquema  
  
1.  En la ventana de propiedades del documento, haga clic en el botón del campo **Esquemas**.  
  
2.  Haga clic en **Agregar**.  
  
     De este modo se abre el cuadro de diálogo **Abrir esquema XSD**.  
  
3.  Busque y seleccione los esquemas que se van a agregar a la caché de esquema.  
  
4.  Haga clic en **Abrir**.  
  
     El esquema se agrega a la caché de esquema y el valor de la columna **Usar** se establece en **Utilizar este esquema**.  
  
### Para eliminar un esquema XML de la caché de esquema  
  
1.  En la ventana de propiedades del documento, haga clic en el botón del campo **Esquemas**.  
  
2.  Seleccione el esquema que desee quitar y haga clic en **Quitar**.  
  
     El esquema se quita de la caché de esquema en memoria, pero no del sistema de archivos.  
  
    > [!NOTE]
    >  Si todavía existe una referencia al esquema a través de un atributo `schemaLocation` o una coincidencia con `targetNamespace`, entonces **Quitar** no funcionará en esta situación debido a una asociación automática.En este caso, se recomienda marcar el esquema como **No utilizar esquemas seleccionados** en la columna **Usar**.  
  
## Vea también  
 [Caché de esquema](../xml-tools/schema-cache.md)   
 [Cuadro de diálogo Esquemas XML](../xml-tools/xml-schemas-dialog-box.md)   
 [Editor XML](../xml-tools/xml-editor.md)