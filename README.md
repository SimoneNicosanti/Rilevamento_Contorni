# Rilevamento_Contorni

def rilevamentoContorni(immagine, DISTANZA_MINIMA_COLORI):
# @param immagine : picture
# @return canvas : picture
  altezzaImmagine = getHeight(immagine)
  lunghezzaImmagine = getWidth(immagine)
  canvas = makeEmptyPicture(lunghezzaImmagine, altezzaImmagine + 1)
  copia(immagine,canvas, 0, 0)
  for x in range(0, lunghezzaImmagine):
    for y in range(0, altezzaImmagine, 2):
        pixelUno = getPixel(canvas, x, y)
        pixelDue = getPixel(canvas, x, y + 1)
        coloreUno = getColor(pixelUno)
        coloreDue = getColor(pixelDue)
        distanzaColori = distance(coloreUno, coloreDue)
        if distanzaColori >= DISTANZA_MINIMA_COLORI:
          setColor(pixelUno, white)
          setColor(pixelDue, black)
        else:
          setColor(pixelUno, white)
          setColor(pixelDue, white)
  show(canvas)
  return canvas
