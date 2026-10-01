# Standalone image for hosting the MCP server outside Agent Manager, as the
# hotel-tools MCP proxy's upstream. On the AWS demo VM it runs as:
#   docker run -d --name hotel-mcp-server --restart unless-stopped \
#     -p <private-ip>:8765:8000 -e PORT=8000 -e PUBLIC_SCHEME=http \
#     -e "PUBLIC_HOST=<public-ip>,<public-ip>:8765" hotel-mcp-server:latest
# with the security group allowing 8765 only from the VM's own Elastic IP.
FROM python:3.11-slim
WORKDIR /app
COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt
COPY server.py hotel_data.py ./
USER nobody
EXPOSE 8000
CMD ["python", "server.py"]
