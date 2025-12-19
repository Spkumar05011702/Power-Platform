## Power Automate 

  https://www.youtube.com/watch?v=qLADf8ne5qQ
  
  Download Error Handling Power Automate flow Template ⬇️
  
  [https://github.com/rdorrani/Microsoft...](https://github.com/rdorrani/Microsoft-Flow/blob/master/FlowTemplatewithErrorHandling_20221030232702.zip)
  
  ## Power Automate flow run URL:
  concat('https://make.powerautomate.com/environments/', workflow()?['tags']['environmentName'], '/flows/', workflow()?['name'], '/runs/', workflow()?['run']['name'])

  ## Filter Query Expression to check if Try Scope action has Failed or TimedOut:
  @or(equals(item()?['Status'], 'Failed'),equals(item()?['Status'], 'TimedOut'))

  Table Style 🖌️ (Included in template)
  [https://github.com/rdorrani/Microsoft...](https://github.com/rdorrani/Microsoft-Flow/blob/master/FlowTemplatewithErrorHandling_20221030232702.zip)

# logicexpressions
  https://aka.ms/logicexpressions#join
