from docx import Document
from docx.shared import Pt
from docx.shared import Inches
from docx.enum.text import WD_PARAGRAPH_ALIGNMENT
from docx.oxml import parse_xml
from docx.oxml.ns import nsdecls

# Crear un nuevo documento de Word
doc = Document()

# Agregar el código HTML dentro de un párrafo
html_code = """
<table>
<tr>
<th>Peligro – Según GTC 45</th>  
<th>Descripción del peligro</th>
<th>Consecuencia para el trabajador</th>
<th>Acción de mejora</th>
</tr>

<!-- Más filas de la tabla aquí -->

</table>
"""

# Crear un párrafo para insertar el código HTML
paragraph = doc.add_paragraph()
run = paragraph.add_run()

# Insertar el código HTML en el párrafo
xml_code = parse_xml(html_code)
run._r.append(xml_code)

# Guardar el documento de Word
doc.save("tabla.docx")
