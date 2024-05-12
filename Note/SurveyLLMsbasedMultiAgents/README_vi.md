# Large Language Model based Multi-Agents: A Survey of Progress and Challenges

## Abstract

LLMs phát triển mạnh mẽ trong thời gian gần đây

-> Tăng khả năng xử lý nhiều nhiệm vụ tự động

-> Không chỉ dựa trên một mô hình LLMs để đưa ra các tác động hay là đưa ra quyết định

-> Sự phát triển của LLMs-based multi-agent

Bài báo đi sâu hơn nhiều với mục tiêu để làm sáng tỏ một số vấn đề sau:

- Các lĩnh vực và môi trường dành cho multiAgents tương tác
- Agents Profiled and Cách các Agents giao tiếp với nhau
- Các cơ chế dùng để phát triển các agents

## Summary

### Agent-Enviroment Interface

The operational environments defines the specific contexts or
settings in which the LLM-MA systems are deployed and
interact

-> Được hiểu đơn giản là việc các Agents tương tác với môi trường xung quanh thông qua các hành động, giao tiếp và cảm nhận. Làm rõ hơn nữa thì nó có bao gồm một số khía cạnh sau:

- Cách các Agents nhận thông tin từ môi trường
- Cách các Agents tương tác với môi trường
- Cách môi trường phản ứng lại với các hành động của các tác nhân

The LLM-based agents perceive and act within
the environment, which in turn influences their behavior and
decision making

-> Đề cập đến mối liên hệ giữa LLM-based Agents và Môi trường (Env)
-> Agents thì sẽ có những quyết định và tương tác ở
