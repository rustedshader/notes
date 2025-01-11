# GO

We use strings.Builder for efficient string concatenation

example

 var sb strings.Builder
	sb.WriteString(API_ROOT_URL)
	sb.WriteString("/annotation/?query=")

	params := make([]string, 0)

	if opts.Entity != "" {
		params = append(params, "entity:"+url.QueryEscape(opts.Entity))
	}
	if opts.Id > 0 {
		params = append(params, fmt.Sprintf("id:%d", opts.Id))
	}
	if opts.Name != "" {
		params = append(params, "name:"+url.QueryEscape(opts.Name))
	}
	if opts.AnnotationContent != "" {
		params = append(params, "text:"+url.QueryEscape(opts.AnnotationContent))
	}
	if opts.Type != "" {
		params = append(params, "type:"+url.QueryEscape(string(opts.Type)))
	}

	sb.WriteString(strings.Join(params, " AND "))

	return sb.String(), nil
