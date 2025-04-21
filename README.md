# DANG
TRO LY DANG AI
// File: ChatBox.jsx

import React, { useState } from "react";

export default function ChatBox() {
  const [messages, setMessages] = useState([
    { sender: "bot", text: "Xin chào! Tôi là Trợ lý Đảng viên AI. Bạn muốn hỏi gì về Điều lệ Đảng, nghị quyết, hay mẫu văn bản?" },
  ]);
  const [input, setInput] = useState("");

  const handleSend = () => {
    if (!input.trim()) return;

    const userMessage = { sender: "user", text: input };
    setMessages((prev) => [...prev, userMessage]);

    // Giả lập trả lời từ trợ lý
    const botReply = getBotReply(input);
    setMessages((prev) => [...prev, { sender: "bot", text: botReply }]);

    setInput("");
  };

  const getBotReply = (question) => {
    question = question.toLowerCase();

    if (question.includes("điều lệ")) {
      return "Điều lệ Đảng hiện hành có 12 chương và 48 điều, được thông qua tại Đại hội XIII.";
    } else if (question.includes("nguyên tắc tổ chức")) {
      return "Nguyên tắc tổ chức cơ bản của Đảng là tập trung dân chủ.";
    } else if (question.includes("kết nạp đảng")) {
      return "Quy trình kết nạp Đảng gồm: giới thiệu – xét duyệt – học cảm tình – hoàn thiện hồ sơ – tổ chức lễ kết nạp.";
    } else if (question.includes("biên bản sinh hoạt")) {
      return "Mẫu biên bản sinh hoạt gồm: thời gian, địa điểm, nội dung thảo luận, ý kiến góp ý, kết luận của chi ủy.";
    } else {
      return "Xin lỗi, tôi chưa có thông tin về nội dung đó. Bạn có thể hỏi về Điều lệ, nghị quyết, hoặc quy trình công tác Đảng.";
    }
  };

  return (
    <div className="max-w-md mx-auto p-4 bg-white rounded-2xl shadow-lg">
      <h1 className="text-xl font-bold mb-4">💬 Trợ lý Đảng viên AI</h1>
      <div className="h-80 overflow-y-scroll border p-3 mb-4 rounded">
        {messages.map((msg, index) => (
          <div
            key={index}
            className={`mb-2 ${
              msg.sender === "user" ? "text-right" : "text-left"
            }`}
          >
            <span
              className={`inline-block px-3 py-2 rounded-xl ${
                msg.sender === "user"
                  ? "bg-blue-500 text-white"
                  : "bg-gray-100 text-black"
              }`}
            >
              {msg.text}
            </span>
          </div>
        ))}
      </div>
      <div className="flex gap-2">
        <input
          type="text"
          value={input}
          onChange={(e) => setInput(e.target.value)}
          placeholder="Nhập câu hỏi..."
          className="flex-1 border rounded-xl px-3 py-2"
        />
        <button
          onClick={handleSend}
          className="bg-green-600 text-white px-4 py-2 rounded-xl"
        >
          Gửi
        </button>
      </div>
    </div>
  );
}
