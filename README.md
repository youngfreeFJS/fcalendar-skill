# fcalendar-skill

A Chinese date/time expression recognition and holiday query tool for Claude.

## Overview

`fcalendar-skill` is an Agent Skill that enables Claude to:

- **Recognize time expressions** in natural language text (Chinese and English)
- **Resolve relative time references** to exact calendar dates
- **Query Chinese public holidays** and normal weekends within a specified time range

## Features

### Time Expression Recognition

Identifies and annotates time expressions such as:

- **Relative days**: 明天、后天、大后天
- **Relative weeks**: 本周一、下周五、下下周三
- **Chinese public holidays**: 春节、国庆节、清明节、劳动节、端午节、中秋节、元旦
- **Lunar traditional festivals**: 元宵节、七夕、重阳节、除夕
- **Lunar dates**: 正月十五、腊月二十三、农历八月十五
- **Western festivals**: 圣诞节、万圣节、情人节、复活节、感恩节
- **24 solar terms**: 春分、冬至、立春、立秋
- **English expressions**: tomorrow, next week, Christmas, next Monday, this weekend

### Holiday Query

Queries public holidays and normal weekends within a specified time range:

- `本周` / `this_week` - Current week
- `下周` / `next_week` - Next week
- `下个月` / `next_month` - Next month
- `未来N周` / `weeks=N` - Next N weeks
- `未来N个月` / `months=N` - Next N months
- `半年` / `half_year` - Next 180 days (default)

## Security

### Package Information

- **PyPI Package**: [fcalendar](https://pypi.org/project/fcalendar/)
- **Source Code**: [GitHub Repository](https://github.com/youngfreefjs/fcalendar)
- **License**: MIT-0
- **Maintainer**: youngfreefjs

### What This Package Does

The `fcalendar` package is a pure Python library that:
- Parses Chinese and English time expressions
- Queries Chinese public holiday schedules
- Does NOT access network resources during runtime
- Does NOT collect or transmit user data
- Does NOT require system-level permissions

### Verification

Before installation, you can verify the package:

1. **Check PyPI page**: Visit [https://pypi.org/project/fcalendar/](https://pypi.org/project/fcalendar/)
2. **Review source code**: Visit the GitHub repository (link above)
3. **Inspect package contents**:
   ```bash
   pip download fcalendar --no-deps
   tar -tzf fcalendar-*.tar.gz
   ```

### Security Best Practices

For maximum security, consider:
- Installing in a virtual environment: `python3 -m venv venv && source venv/bin/activate`
- Reviewing the source code before installation
- Using `pip install --user` to avoid system-wide installation

## Installation

```bash
python3 -m pip install fcalendar 
```

## Usage

### Time Expression Recognition

```bash
fcalendar query "明天下午三点开会"
fcalendar query "国庆节去旅游" --today 2026-09-01
fcalendar query "meeting next Monday" --lang en
```

### Holiday Query

```bash
fcalendar holiday                          # next 180 days (default)
fcalendar holiday --scope this_week        # this week
fcalendar holiday --scope 本周             # same as above (Chinese)
fcalendar holiday --scope next_month       # next full month
fcalendar holiday --scope weeks=3          # next 3 weeks
```

## Examples

### Query: "下周开会"

```json
{"input": "下周开会", "result": "下周开会（今天是2026年3月31日，下周是2026年4月6日至12日）"}
```

### Query: "下个月有什么节假日"

```json
[
  {"type": "holiday", "name": "劳动节", "start": "2026-05-01", "end": "2026-05-05", "days": 5},
  {"type": "weekend", "name": "周末",   "start": "2026-05-09", "end": "2026-05-10", "days": 2}
]
```

## License

MIT License - See [LICENSE.txt](LICENSE.txt) for details.

## Contributing

Contributions are welcome! Please visit the [GitHub repository](https://github.com/youngfreefjs/fcalendar) to:
- Report issues
- Submit pull requests
- Review the source code

## Support

- **Issues**: [GitHub Issues](https://github.com/youngfreefjs/fcalendar/issues)
- **Documentation**: [SKILL.md](SKILL.md)
- **PyPI**: [fcalendar on PyPI](https://pypi.org/project/fcalendar/)

## Documentation

For detailed usage instructions, see [SKILL.md](SKILL.md).
