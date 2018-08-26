---
layout: post
title:  "UITableView Leading, Trailing Swipe Action"
date:   2018-08-26 16:00:00 +0900
tag: [iOS]
---

# UITableView Swipe Actions

---

>TableView 에서 라이브러리를 사용하지 않고 Swipe 액션을 구현해 봅니다.

---

## UITableViewDelegate 메서드

iOS 11 부터 두 가지 UITableViewDelegate 메서드를 사용할 수 있습니다. 아래의 두 메서드를 사용하면 스와이프 액션을 쉽게 구현할 수 있습니다.

```
optional func tableView(_ tableView: UITableView, 
leadingSwipeActionsConfigurationForRowAt indexPath: IndexPath) -> UISwipeActionsConfiguration?

optional func tableView(_ tableView: UITableView, 
trailingSwipeActionsConfigurationForRowAt indexPath: IndexPath) -> UISwipeActionsConfiguration?

```

이 두 메서드는 **leading, trailing swipe action** 을 리턴 합니다.


## UISwipeActionsConfiguration

UISwipeActionsConfiguration 은 UIContextualAction 들을 포함하는 클래스 입니다. 접근가능한 프로퍼디로 
`var performsFirstActionWithFullSwipe: Bool` 가 있습니다.

## UIContextualAction

초기화 메서드는 아래의 코드로 style 과 title, handler 로 초기화 할 수 있습니다.

```
init(style: UIContextualAction.Style, title: String?, handler: UIContextualAction.Handler)
```

```
let share = UIContextualAction(style: .normal, title: "Share") { action, view, completion in
    completion(true)
}
```

위 코드처럼 초기화 하고 사용할 수 있습니다. 그리고 아래와 같은 프로퍼티들을 커스텀해 사용할 수 있습니다.

- `var title: String?`
- `var backgroundColor: UIColor!`
- `var image: UIImage?`
- `var handler: UIContextualAction.Handler`

# Implementation

```

override func tableView(_ tableView: UITableView, trailingSwipeActionsConfigurationForRowAt indexPath: IndexPath) -> UISwipeActionsConfiguration? {

    let share = UIContextualAction(style: .normal, title: "Share") { action, view, completion in
        completion(true)
    }

    let delete = UIContextualAction(style: .destructive, title: "Delete") { [weak self] action, view, completion in
        self?.langs.remove(at: indexPath.row)
        tableView.deleteRows(at: [indexPath], with: UITableViewRowAnimation.automatic)
        completion(true)
    }

    delete.image = #imageLiteral(resourceName: "trash")

    return UISwipeActionsConfiguration(actions: [delete, share])
}

override func tableView(_ tableView: UITableView, leadingSwipeActionsConfigurationForRowAt indexPath: IndexPath) -> UISwipeActionsConfiguration? {
    let like = UIContextualAction(style: .normal, title: "Like") { [weak self] action, view, completion in
        guard let `self` = self else {
            return
        }
        self.langs[indexPath.row].liked = !self.langs[indexPath.row].liked
        completion(true)
    }

    like.image = langs[indexPath.row].liked ? #imageLiteral(resourceName: "filledLike") : #imageLiteral(resourceName: "like")
    like.backgroundColor = UIColor.darkGray

    return UISwipeActionsConfiguration(actions: [like])
}
```

