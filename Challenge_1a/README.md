# Adobe - Connecting the Dots Challenge (Round 1A)

## How to Run

### Build Docker Image
```
docker build --platform linux/amd64 -t adobe-outline-extractor .
```

### Run the Solution
```
docker run --rm -v $(pwd)/input:/app/input -v $(pwd)/output:/app/output --network none adobe-outline-extractor
```

### Input
Put your `.pdf` files in `/input`

### Output
Extracted outline will be in `/output` as `.json` files

## Output Format
```json
{
  "title": "Document Title",
  "outline": [
    { "level": "H1", "text": "Heading One", "page": 1 },
    { "level": "H2", "text": "Subheading", "page": 2 }
  ]
}
```
