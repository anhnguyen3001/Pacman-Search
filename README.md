# Pacman-Search
Câu 1: DepthFirstSearch:
- Cấu trúc dữ liệu: Stack lưu (state, list actions đến state của node con từ node cha).
- Cài đặt: Chạy vòng lặp hết Stack, lấy ra x,y,actions từ node cuối của Stack. Kiểm tra xem x,y có phải state đích. Nếu không, kiểm tra xem đã thăm chưa. Nếu chưa thăm thì thêm vào list vị trí đã thăm rồi push các node được phát triển từ node hiện tại.

Câu 2: BreadthFirstSearch:
<br />Tương tự DFS, ngoại trừ sử dụng Queue để lưu (state, list actions)

Câu 3: UniformCostSearch:
<br />Cài đặt khá tương tự DFS, BFS, nhưng sử dụng PriorityQueue để lưu (state, list actions, cost). PriorityQueue với mức độ ưu tiên là cost(startState -> thisState).

Câu 4: AStarSearch:
<br />Cài đặt tương tự UCS nhưng độ ưu tiên của PriorityQueue = cost(startState -> thisState) + heuristic (hàm ước lượng)

Câu 5: CornersProblem:
- Problem có state = (position, list foundCorners)
- Hàm getStartState: trả về vị trí bắt đầu và list foundCorners là []
- Hàm isGoalState: kiểm tra xem list foundCorners có độ dài = 4 không? Nghĩa là cả 4 góc đã được thăm.
- Hàm getSuccessors: Chạy vòng lặp với 4 hướng đi từ vị trí hiện tại (lên trên, sang phải, xuống dưới, sang trái). Mỗi hướng sẽ tính vị trí, kiểm tra vị trí đó có phải tường không? Nếu không phải tường, kiểm tra xem có phải góc không và đã được thăm chưa? Nếu là góc và chưa được thăm thì thêm vào list foundCorner. Sau đó thêm vào list successors (state, action, 1) 

Câu 6: CornersHeuristic:
<br />Tính tổng manhattan của vị trí hiện tại đến tất cả các góc chưa được thăm. 
Trước hết là tìm ra các góc chưa được thăm. Sau đó chạy hết list góc đó, tính khoảng cách manhattan từ position đến tất cả corners chưa thăm. Với lần chạy đầu thì position = vị trí hiện tại, sau đó sau mỗi lần chạy thì position = corner với khoảng cách manhattan min. Mỗi lần tìm ra corner với khoảng cách min thì remove corner khỏi list corner chưa thăm.

Câu 7: FoodHeuristic:
<br />heuristic = khoảng cách bfs giữa hạt đồ ăn xa nhất với vị trí pacman hiện tại.

Câu 8: Suboptimal Search:
- Định nghĩa goalState (của AnyFoodSearchProblem): xem vị trí hiện tại có chưa hạt đồ ăn không?
- Hàm findPathToClosestDot: sử dụng lại thuật toán tìm kiếm bfs
