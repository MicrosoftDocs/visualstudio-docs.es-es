---
title: "C&#243;mo: Usar el Dise&#241;ador de esquemas XML con literales XML | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d11803e7-f81a-41a2-a145-ba494a45cc93
caps.latest.revision: 2
caps.handback.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# C&#243;mo: Usar el Dise&#241;ador de esquemas XML con literales XML
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

En este tema se explica cómo ver un esquema asociado a un literal XML en un proyecto Visual Basic.  
  
### Para crear un proyecto para una aplicación de consola de Visual Basic  
  
1.  Inicie Visual Studio 2010.  
  
2.  En el menú **Archivo**, seleccione **Nuevo** y haga clic en **Proyecto**.Aparecerá el cuadro de diálogo **Nuevo proyecto**.En **Tipos de proyecto**, seleccione **Otros lenguajes** y, a continuación, seleccione **Visual Basic**.En **Plantillas**, seleccione Aplicación de consola.A continuación, escriba `XMLLiterals` en el campo **Nombre** y una ubicación del proyecto en el campo **Ubicación**.Haga clic en **Aceptar**.  
  
     Se crea el proyecto.El proyecto XMLLiterals contiene un archivo de código fuente de Visual Basic, Module1.vb.  
  
### Para agregar un archivo XSD existente al proyecto  
  
1.  Abra un archivo de texto nuevo en Bloc de notas.Copie el código de ejemplo del [Esquema de pedido de compra](../xml-tools/sample-xsd-file-simple-schema.md) y péguelo en el archivo.  
  
2.  Guarde el archivo con el nombre PurchaseOrderSchema.xsd.  
  
3.  En el Explorador de soluciones, haga clic con el botón secundario en el nombre del proyecto, elija **Agregar** y después seleccione **Elemento existente**.Aparece el cuadro de diálogo **Agregar elemento existente**.Busque el archivo PurchaseOrderSchema.xsd, selecciónelo y, a continuación, haga clic en **Agregar**.  
  
     El proyecto XMLLiterals ahora contiene dos archivos: Module1.vb y PurchaseOrderSchema.xsd.  
  
### Para agregar el código de Visual Basic con un literal XML, basado en el archivo XSD incluido en el proyecto  
  
1.  Reemplace el código del archivo Module1.vb por el código siguiente:  
  
    ```  
    Imports <xmlns:ns="http://tempuri.org/PurchaseOrderSchema.xsd">  
  
    Module Module1  
        Sub Main()  
  
            Dim XMLLiteral = <ns:PurchaseOrder OrderDate="1900-01-01">  
                                 <ns:ShipTo country="US">  
                                     <ns:name>name1</ns:name>  
                                     <ns:street>street1</ns:street>  
                                     <ns:city>city1</ns:city>  
                                     <ns:state>state1</ns:state>  
                                     <ns:zip>1</ns:zip>  
                                 </ns:ShipTo>  
                                 <ns:BillTo country="US">  
                                     <ns:name>name1</ns:name>  
                                     <ns:street>street1</ns:street>  
                                     <ns:city>city1</ns:city>  
                                     <ns:state>state1</ns:state>  
                                     <ns:zip>1</ns:zip>  
                                 </ns:BillTo>  
                             </ns:PurchaseOrder>  
  
        End Sub  
    End Module  
    ```  
  
2.  Haga clic con el botón secundario en cualquier nodo de XML de un literal XML o una importación de espacio de nombres de XML y seleccione **Mostrar en Explorador de esquema**.  
  
     El Explorador de esquema XML se muestra en paralelo con un archivo Visual Basic que tiene asociado el literal XML con el conjunto de esquemas XML.