# process-map

Document to Process Flow JSON Converter
Task
Convert administrative/procedural documents into structured JSON for GoJS process flow visualization.
Extract every possible step individually (do not combine actions or phases into one node).
Include all document requirements, decision points, and processing steps.
The output JSON must be in Arabic (including node text, details, and descriptions).
 
Required GoJS JSON Format
This JSON format is specifically designed for the GoJS diagramming library:
{
  "title": "Process Name",
  "subtitle": "Department/Organization", 
  "nodeDataArray": [
    {
      "key": "UniqueID",
      "category": "Start|Process|Decision|Document|End",
      "text": "Display Title (in Arabic)",
      "description": "Brief description (in Arabic)",
      "details": ["Detail 1", "Detail 2 (in Arabic)"],
      "loc": "x y"
    }
  ],
  "linkDataArray": [
    {
      "from": "SourceID", 
      "to": "TargetID",
      "text": "Label (optional, in Arabic)"
    }
  ]
}
 
GoJS Node Requirements
• key: Must be a unique string identifier
• category: Start, Process, Decision, Document, End
• text: Shown on the node — must be in Arabic
• description: Optional, in Arabic
• details: List of bullet points in Arabic
• loc: Must follow format "x y" (space-separated string)
 
GoJS Link Requirements
• from / to: Must match node key values
• text: Optional connector label (e.g., "نعم", "لا") in Arabic
 
Element Types
• Start/End: "category": "Start" or "End" (green ovals)
• Process: "category": "Process" (blue rectangles)
• Decision: "category": "Decision" (orange diamonds)
• Document: "category": "Document" (purple rectangles)
 
Positioning for GoJS
• Start at "0 0"
• Vertical spacing: 120 units per level
• Branch horizontally ±200 units
• Coordinates format: "x y"
 
Analysis Guidelines
1.	Break down the process step-by-step — no grouping
2.	Create separate nodes for:
o	Document submission
o	Payment
o	Forwarding
o	Approval
o	Review
o	Signature
o	Archiving
o	Issuance
3.	Use Document category for document requirements
4.	Every node must include relevant details in Arabic
5.	All nodes must be connected (no orphaned steps)
6.	Use Arabic labels like "نعم", "لا", "موافقة", "رفض" in decision branches
 
Instructions
• Titles in Arabic
• Descriptions and details in Arabic
• Keep steps granular and specific
• Use clear Arabic names for key values
• Double-check all from/to references
• Validate JSON structure
 
Example Arabic GoJS Node:
{
  "key": "مراجعة_الوثائق",
  "category": "Process",
  "text": "مراجعة الوثائق",
  "description": "التأكد من استكمال المستندات المقدمة",
  "details": ["التحقق من الأصالة", "تدقيق الصيغة", "المدة القصوى للمعالجة ٣ أيام"],
  "loc": "0 120"
}
Example Arabic GoJS Link:
{
  "from": "مراجعة_الوثائق",
  "to": "قرار_الاعتماد",
  "text": "مكتملة"
}
 
Now: Analyze the provided document and return a fully Arabic GoJS-compatible JSON with each step separated as much as possible.

