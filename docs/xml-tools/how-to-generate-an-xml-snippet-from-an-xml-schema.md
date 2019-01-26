---
title: Procedimiento Generar un fragmento de código XML a partir de un esquema XML
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
ms.assetid: 2c128d2a-aaa6-4814-aa95-e07056afe338
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 54f8a689c83fc0eb370e2e48a9421071151c9271
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "55030436"
---
# <a name="how-to-generate-an-xml-snippet-from-an-xml-schema"></a>Procedimiento Generar un fragmento XML desde un esquema XML

Con el Editor XML es posible generar fragmentos de código XML a partir de un esquema de lenguaje de definición de esquema XML (XSD). Por ejemplo, durante la creación de un archivo XML, mientras se coloca junto al nombre del elemento, puede presionar **ficha** para rellenar el elemento con los datos XML generados a partir de la información de esquema de ese elemento.

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

 Los pasos descritos en esta sección muestran cómo usar el fragmento XML generados por esquema, característica del Editor XML.

> [!NOTE]
> Antes de comenzar estos procedimientos, guarde el archivo de esquema en el equipo local.

### <a name="to-create-a-new-xml-file-and-associate-it-with-an-xml-schema"></a>Para crear un nuevo archivo XML y asociarlo con un esquema XML

1.  En el **archivo** menú, elija **New**y haga clic en **archivo**.

2.  Seleccione **archivo XML** en el **plantillas** panel y haga clic en **abierto**.

     Se abre un nuevo archivo en el editor. El archivo contiene una declaración XML predeterminada, `<?xml version="1.0" encoding="utf-8">`.

3.  En la ventana Propiedades del documento, haga clic en el botón Examinar (**...** ) en el **esquemas** campo.

     El **esquemas XSD** se muestra el cuadro de diálogo.

4.  Haga clic en **Agregar**.

     El **Abrir esquema XSD** se muestra el cuadro de diálogo.

5.  Seleccione el archivo de esquema y haga clic en **abierto**.

6.  Haga clic en **Aceptar**.

     El esquema XML está ahora asociado con el documento XML.

### <a name="to-generate-an-xml-snippet"></a>Para generar un fragmento de código XML

1.  Escriba `<` en el panel del editor.

2.  La lista de miembros muestra los elementos posibles:

     **!--** para agregar un comentario.

     **! DOCTYPE** para agregar un tipo de documento.

     **?** para agregar una instrucción de procesamiento.

     **Póngase en contacto con** para agregar el elemento raíz.

3.  Seleccione **póngase en contacto con** en la lista de miembros y presione **ENTRAR**.

     El editor agrega la etiqueta de apertura `<Contact` y coloca el cursor después del nombre del elemento.

4.  Presione **ficha** para generar datos XML para el `Contact` elemento según su información de esquema.

## <a name="input"></a>Entrada

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

 Estos son los datos XML que se generan en función de la información de esquema asociada con el elemento `Contact`. Los elementos marcados como `bold` designan campos editables en el fragmento XML.

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

- [Fragmentos XML](../xml-tools/xml-snippets.md)
- [Cómo: Utilizar fragmentos XML](../xml-tools/how-to-use-xml-snippets.md)