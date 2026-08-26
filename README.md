# adg-media

Statische mediahosting voor adggroep.nl. Elk bestand hier is direct opvraagbaar
via GitHub Pages, zodat CMS-velden die om een `Video URL (mp4)` vragen een
werkende link krijgen.

## Structuur

- `video/` — H.264 mp4, 1080p, faststart aan
- `poster/` — bijbehorende stilstaande beelden

## Nieuwe video toevoegen

```bash
ffmpeg -i origineel.mov -c:v libx264 -crf 24 -preset slow -profile:v high \
       -pix_fmt yuv420p -vf "scale=1920:-2" -movflags +faststart \
       -c:a aac -b:a 128k video/naam.mp4
git add video/naam.mp4 && git commit -m "naam.mp4 toevoegen" && git push
```

Na de push staat hij binnen een minuut op
`https://marketingadg.github.io/adg-media/video/naam.mp4`.
