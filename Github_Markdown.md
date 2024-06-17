# Github_Markdown
> 간단한 텍스트를 스타일링하기 좋은 도구
>

### 1. 제목 (Headers)
Markdown에서는 `#` 문자를 사용하여 제목을 생성할 수 있다.<br> `#`의 개수에 따라 제목의 크기가 달진다.

```markdown
# 제목 1
## 제목 2
### 제목 3
#### 제목 4
##### 제목 5
###### 제목 6
```

### 2. 텍스트 스타일링

- **굵게 (Bold)**: 텍스트를 굵게 하려면 `**` 또는 `__`로 감싼다.
  ```markdown
  **굵게**
  __굵게__
  ```

- *기울임체 (Italic)*: 텍스트를 기울임체로 하려면 `*` 또는 `_`로 감싼다.
  ```markdown
  *기울임체*
  _기울임체_
  ```

- ~~취소선 (Strikethrough)~~: 텍스트에 취소선을 적용하려면 `~~`로 감싼다.
  ```markdown
  ~~취소선~~
  ```

### 3. 인용문 (Blockquotes)
인용문은 `>`를 사용하여 생성할 수 있다.

```markdown
> 이것은 인용문입니다.
> 여러 줄로도 가능합니다.
```

### 4. 목록 (Lists)
Markdown은 순서 있는 목록과 순서 없는 목록을 지원한다.

- **순서 없는 목록 (Unordered Lists)**: `*`, `+`, 또는 `-`을 사용하여 항목을 나열한다.
  ```markdown
  - 항목 1
  - 항목 2
    - 하위 항목 1
    - 하위 항목 2
  ```

- **순서 있는 목록 (Ordered Lists)**: 숫자를 사용하여 항목을 나열한다.
  ```markdown
  1. 첫 번째 항목
  2. 두 번째 항목
     1. 하위 항목 1
     2. 하위 항목 2
  ```

### 6. 표 (Tables)

```markdown
| 헤더1 | 헤더2 |
|-------|-------|
| 셀1   | 셀2   |
| 셀3   | 셀4   |
```

### 7. 수평선 (Horizontal Rules)
수평선을 그리려면 세 개 이상의 `-`, `*`, 또는 `_`를 사용한다.

```markdown
---
***
___
```

### 8. 체크리스트 (Task Lists)
체크리스트를 만들려면 `- [ ]` 또는 `- [x]`를 사용한다. <br>
```markdown
- [x] 완료된 작업
- [ ] 미완료된 작업
```

### 9. HTML 사용
Markdown에서는 HTML 태그를 직접 사용할 수도 있습니다.

```markdown
<p>This is an HTML paragraph.</p>
```

이것은 GitHub Markdown의 기본적인 문법입니다. 이를 조합하여 문서를 효과적으로 구성할 수 있습니다. GitHub에서는 README 파일 작성, Issue 및 Pull Request 설명 작성 등에 Markdown을 많이 사용합니다.

### 10. 이미지 삽입 
```markdown
    <img src="<imagePath>" width="<size>" height="<size>">
    // 이미지 중앙 정렬
    <center> <img src="<imagePath>" width="<size>" height="<size>"> </center>
```

Link
---

### 1. 링크 삽입
링크를 삽입하는 방법입니다.

- **일반 링크**: `[링크 텍스트](URL)` 형식을 사용합니다.
  ```markdown
  [GitHub](https://github.com)
  ```

- **이미지 링크**: `![대체 텍스트](이미지 URL)` 형식을 사용합니다.
  ```markdown
  ![GitHub Logo](https://github.githubassets.com/images/modules/logos_page/GitHub-Mark.png)
  ```

### 2. Gist, Issue, Pull Request, Commit 자동 링크 변환
GitHub 내의 특정 요소들은 자동으로 링크로 변환됩니다. 예를 들어, Gist, Issue, Pull Request, Commit의 ID 등을 입력하면 자동으로 해당 항목으로 연결됩니다.

- **Gist**: `gist:123456` (Gist의 ID를 입력)
- **Issue**: `#123` (리포지토리의 이슈 번호)
- **Pull Request**: `#123` (리포지토리의 풀 리퀘스트 번호)
- **Commit**: `commit_hash` (커밋 해시를 입력)

```markdown
Refer to issue #123 for more details.
```

이 예에서는 `#123`이 자동으로 해당 Issue로 링크됩니다.

### 3. YouTube 및 기타 미디어의 미리보기 링크
GitHub에서 직접 미디어를 임베드할 수는 없지만, 일부 URL을 포함하면 해당 URL에 대한 미리보기가 제공됩니다. 예를 들어 YouTube 동영상 URL을 포함하면, URL 옆에 동영상 미리보기가 표시됩니다.

```markdown
Check out this video: https://www.youtube.com/watch?v=dQw4w9WgXcQ
```

GitHub Issue, Pull Request, 또는 댓글에서 위와 같이 YouTube URL을 추가하면 해당 링크가 미리보기와 함께 표시됩니다.

### 4. Emoji 사용
GitHub에서는 텍스트에 이모지를 추가하여 커뮤니케이션을 생동감 있게 만들 수 있습니다. 이모지는 `:emoji_name:` 형식으로 입력합니다.

```markdown
:smile: :tada: :rocket:
```

이렇게 하면 텍스트에 이모지가 표시됩니다.

### 5. Task Lists (체크리스트)
Markdown에서 체크리스트를 사용하여 작업 상태를 표시할 수 있습니다.

```markdown
- [x] Task 1
- [ ] Task 2
- [ ] Task 3
```

이렇게 하면 체크리스트 항목들이 표시됩니다.

### 6. @멘션 및 팀 멘션
GitHub에서는 `@username` 형식을 사용하여 특정 사용자를 언급하거나, `@org/team-name` 형식으로 팀을 언급할 수 있습니다. 이는 해당 사용자나 팀에게 알림을 보냅니다.

```markdown
Hey @octocat, please review this.
```

### 7. Reference-Style Links
다양한 곳에서 반복해서 사용할 링크를 정의하고 참조 스타일로 사용할 수 있습니다.

```markdown
This is [an example][example].

[example]: https://www.example.com
```

이렇게 하면 여러 번 사용할 링크를 관리하기 쉽게 만들 수 있습니다.

---

###### References
[이미지 삽입 및 사이즈 조절](https://kyounghwan01.github.io/blog/etc/md-img-insert-resize/#img-tag-%E1%84%8B%E1%85%B5%E1%84%8B%E1%85%AD%E1%86%BC%E1%84%92%E1%85%A1%E1%84%86%E1%85%A7-%E1%84%8B%E1%85%B5%E1%84%86%E1%85%B5%E1%84%8C%E1%85%B5-%E1%84%89%E1%85%A1%E1%86%B8%E1%84%8B%E1%85%B5%E1%86%B8-%E1%84%86%E1%85%B5%E1%86%BE-%E1%84%89%E1%85%A1%E1%84%8B%E1%85%B5%E1%84%8C%E1%85%B3-%E1%84%8C%E1%85%A9%E1%84%8C%E1%85%A5%E1%86%AF)