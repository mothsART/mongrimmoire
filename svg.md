# Utilitaire pour faire du SVG

SVGO :
    time svgo organes.svg organes.svgo.svg
    
SVGCleaner :
    time svgcleaner organes.svg organes.svgcleaner.svg

    // Pour avoir une compression meilleur que svgo :
    svgcleaner --coordinates-precision 2 --properties-precision 2 --transforms-precision 2 --paths-coordinates-precision 2
