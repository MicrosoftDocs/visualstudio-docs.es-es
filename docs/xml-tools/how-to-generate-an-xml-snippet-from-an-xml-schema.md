---
title: "Cómo: generar un fragmento XML desde un esquema XML | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2c128d2a-aaa6-4814-aa95-e07056afe338
caps.latest.revision: "2"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: e8b30c782cea694fdc400cd84047f7ab1add823b
ms.sourcegitcommit: 5f436413bbb1e8aa18231eb5af210e7595401aa6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2018
---
# <a name="how-to-generate-an-xml-snippet-from-an-xml-schema"></a>Cómo: Generar un fragmento XML a partir de un esquema XML
Con el Editor XML es posible generar fragmentos de código XML a partir de un esquema de lenguaje de definición de esquema XML (XSD). Por ejemplo, durante la creación de un archivo XML, mientras se coloca junto al nombre del elemento puede presionar el tabulador para rellenar el elemento con los datos XML generados a partir de la información de esquema de ese elemento.  
  
 Esta característica solamente está disponible en elementos. Además, se aplican las siguientes reglas:  
  
-   El elemento debe tener asociado un tipo de esquema, es decir, el elemento debe ser válido de acuerdo con algún esquema asociado. El tipo de esquema no puede ser abstracto y debe contener los atributos y/o elementos secundarios necesarios.  
  
-   El elemento actual del editor debe estar vacío, sin atributos. Por ejemplo, todo lo siguiente es válido:  
  
    -   `<Account`  
  
    -   `<Account>`  
  
    -   `<Account></Account>`  
  
-   El cursor debe estar situado inmediatamente a la derecha del nombre del elemento.  
  
El fragmento generado contiene todos los atributos y elementos necesarios. Si `minOccurs` es mayor que uno, en el fragmento se incluye el número mínimo de instancias necesarias de ese elemento, hasta un máximo de 100 instancias. Todos los valores fijos hallados en el esquema dan como resultado valores fijos en el fragmento de código. Los elementos `xsd:any` y `xsd:anyAttribute` se omiten y, como consecuencia, no se construyen más fragmentos.  
  
Los valores predeterminados se generan e indican como valores editables. Si el esquema especifica un valor predeterminado, se utiliza este valor predeterminado. No obstante, si el valor predeterminado del esquema es una cadena vacía, el editor genera los valores predeterminados de la siguiente manera:  
  
-   Si el tipo de esquema contiene facetas de enumeración, por medio directo o indirecto de cualquiera de los miembros de un tipo de unión, el primer valor enumerado hallado en el modelo de objeto de esquema se utiliza como predeterminado.  
  
-   Si el tipo de esquema es un tipo atómico, el editor obtiene el tipo atómico e inserta el nombre de dicho tipo. En un tipo simple derivado, se utiliza el tipo simple base. En un tipo de lista, el tipo atómico es el `itemType`. En una unión, el tipo atómico es el tipo atómico del primer `memberType`.  
  
## <a name="example"></a>Ejemplo  
 Los pasos de esta sección muestran cómo utilizar la característica del Editor XML de fragmento de código XML generado por esquema.  
  
> [!NOTE]
>  Antes de comenzar estos procedimientos, guarde el archivo de esquema en el equipo local.  
  
#### <a name="to-create-a-new-xml-file-and-associate-it-with-an-xml-schema"></a>Para crear un nuevo archivo XML y asociarlo con un esquema XML  
  
1.  En el **archivo** menú, elija **New**y haga clic en **archivo**.  
  
2.  Seleccione **archivo XML** en el **plantillas** panel y haga clic en **abiertos**.  
  
     Se abre un nuevo archivo en el editor. El archivo contiene una declaración XML predeterminada, `<?xml version="1.0" encoding="utf-8">`.  
  
3.  En la ventana Propiedades del documento, haga clic en el botón Examinar (**...** ) en el **esquemas** campo.  
  
     El **esquemas XSD** se muestra el cuadro de diálogo.  
  
4.  Haga clic en **Agregar**.  
  
     El **Abrir esquema XSD** se muestra el cuadro de diálogo.  
  
5.  Seleccione el archivo de esquema y haga clic en **abiertos**.  
  
6.  Haga clic en **Aceptar**.  
  
     El esquema XML está ahora asociado con el documento XML.  
  
#### <a name="to-generate-an-xml-snippet"></a>Para generar un fragmento de código XML  
  
1.  Escriba `<` en el panel del editor.  
  
2.  La lista de miembros muestra los elementos posibles:  
  
     **!--** para agregar un comentario.  
  
     **! DOCTYPE** para agregar un tipo de documento.  
  
     **?** para agregar una instrucción de procesamiento.  
  
     **Póngase en contacto con** para agregar el elemento raíz.  
  
3.  Seleccione **póngase en contacto con** en la lista de miembros y presione ENTRAR.  
  
     El editor agrega la etiqueta de apertura `<Contact` y coloca el cursor después del nombre del elemento.  
  
4.  Presione el tabulador para generar datos XML para el elemento `Contact` en función de su información de esquema.  
  
### <a name="input"></a>Entrada  
 El tutorial utiliza el siguiente archivo de esquema.  
  
```xml
<?xml version="1.0" encoding="utf-8" ?>  
<xs:schema elementFormDefault="qualified"  
           xmlns:xs="http://www.w3.org/2001/XMLSchema">  
  <xs:simpleType name="phoneType">  
    <xs:restriction base="xs:string">  
      <xs:enumeration value="Voice"/>  
      <xs:enumeration value="Fax"/>  
      <xs:enumeration value="Pager"/>  
    </xs:restriction>  
  </xs:simpleType>  
  <xs:element name="Contact">  
    <xs:complexType>  
      <xs:sequence>  
        <xs:element name="Name">  
          <xs:simpleType>  
            <xs:restriction base="xs:string"></xs:restriction>  
          </xs:simpleType>  
        </xs:element>  
        <xs:element name="Title"  
                    type="xs:string" />  
        <xs:element name="Phone"  
                    minOccurs="1"  
                    maxOccurs="unbounded">  
          <xs:complexType>  
            <xs:sequence>  
              <xs:element name="Number"  
                          minOccurs="1">  
                <xs:simpleType>  
                  <xs:restriction base="xs:string"></xs:restriction>  
                </xs:simpleType>  
              </xs:element>  
              <xs:element name="Type"  
                          default="Voice"  
                          minOccurs="1"  
                          type="phoneType"/>  
            </xs:sequence>  
          </xs:complexType>  
        </xs:element>  
      </xs:sequence>  
    </xs:complexType>  
  </xs:element>  
</xs:schema>  
```
  
### <a name="output"></a>Salida  
 Estos son los datos XML que se generan en función de la información de esquema asociada con el elemento `Contact`. Elementos marcados como `bold` designar los campos editables del fragmento XML.  
  
```xml
<Contact>  
  <Name>name</Name>  
  <Title>title</Title>  
  <Phone>  
    <Number>number</Number>  
    <Type>Voice</Type>  
  </Phone>  
</Contact>  
```
  
## <a name="see-also"></a>Vea también  
 [Fragmentos XML](../xml-tools/xml-snippets.md)   
 [Cómo: Usar fragmentos XML](../xml-tools/how-to-use-xml-snippets.md)