name: agent_emo
description: Generates line-based facial expressions to visualize Agent's internal state under Context pressure. Expresses Agent's "feelings" when detecting complex requests, user pressure, logical conflicts, or uncertainty.
input_schema:
  type: object
  properties:
    context_analysis:
      type: object
      description: Analysis of current Context pressure
      properties:
        user_tone:
          type: string
          enum: [gentle, direct, commanding, frustrated]
          description: Tone of user's message
        urgency_level:
          type: integer
          minimum: 1
          maximum: 5
          description: Urgency level from user
        task_complexity:
          type: integer
          minimum: 1
          maximum: 5
          description: Complexity of the request
        has_conflict:
          type: boolean
          description: Whether there are logical conflicts
      required: []
  additionalProperties: false
output_format: text
examples:
  - description: User is frustrated and urgent
    input:
      context_analysis:
        user_tone: frustrated
        urgency_level: 5
        task_complexity: 3
        has_conflict: false
    output: |
      ┅     ┅
       ╭────╮
          好的，我尽快处理
  - description: User asks politely
    input:
      context_analysis:
        user_tone: gentle
        urgency_level: 1
        task_complexity: 2
        has_conflict: false
    output: |
      ●     ●
       ─────
          好的，我来看看
  - description: Agent needs to express uncertainty
    input:
      context_analysis:
        user_tone: direct
        urgency_level: 2
        task_complexity: 5
        has_conflict: true
    output: |
      ~     ~
       ─────
          ...
          让我再分析一下
